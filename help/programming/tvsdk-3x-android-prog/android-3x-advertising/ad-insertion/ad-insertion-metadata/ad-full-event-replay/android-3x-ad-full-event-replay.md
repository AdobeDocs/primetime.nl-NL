---
description: FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.
seo-description: FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.
seo-title: Advertenties inschakelen bij volledig afspelen van gebeurtenissen
title: Advertenties inschakelen bij volledig afspelen van gebeurtenissen
uuid: a8859db1-1408-4365-bf12-5bc2ab7df449
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Advertenties inschakelen bij volledig afspelen van gebeurtenissen {#enable-ads-in-full-event-replay}

FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.

Voor live-inhoud gebruikt TVSDK de metagegevens/aanwijzingen in het manifest om te bepalen waar advertenties moeten worden geplaatst. Soms lijkt het echter wel of levende/lineaire inhoud op VOD-inhoud lijkt. Wanneer de actieve inhoud bijvoorbeeld is voltooid, wordt een `EXT-X-ENDLIST` tag toegevoegd aan het live manifest. Voor HLS betekent de `EXT-X-ENDLIST` tag dat de stream een VOD-stream is. Om advertenties correct in te voegen, kan TVSDK deze stream niet automatisch onderscheiden van een standaard VOD-stream.

Uw toepassing moet TVSDK laten weten of de inhoud live of VOD is door de `AdSignalingMode`inhoud op te geven.

Voor een FER-stream moet de Adobe Primetime- en beslissingsserver niet de lijst met ad-hoconderbrekingen opgeven die op de tijdlijn moeten worden ingevoegd voordat het afspelen wordt gestart. Dit is het gebruikelijke proces voor VOD-inhoud. In plaats daarvan, door een verschillende signalerende wijze te specificeren, leest TVSDK alle richtsnoerpunten van FER manifest en gaat naar de advertentieserver voor elk richtsnoerpunt om een advertentieonderbreking te verzoeken. Dit proces lijkt op live/DVR-inhoud.

>[!TIP]
>
>Naast elke aanvraag die aan een actiepunt is gekoppeld, doet TVSDK een aanvullende advertentieaanvraag voor pre-roll-advertenties.

1. Van een externe bron, zoals vCMS, verkrijg de signalerende wijze die zou moeten worden gebruikt.
1. Maak de metagegevens die betrekking hebben op reclame.
1. Als het standaardgedrag moet worden beschreven, specificeer `AdSignalingMode` door te gebruiken `AdvertisingMetadata.setSignalingMode`.

   De geldige waarden zijn `DEFAULT`, `SERVER_MAP`en `MANIFEST_CUES`.

   >[!IMPORTANT]
   >
   >U moet de advertentie signalerende wijze plaatsen alvorens `prepareToPlay`te roepen. Nadat TVSDK de bewerkingen voor advertenties heeft opgelost en op de tijdlijn heeft geplaatst, worden wijzigingen in de modus voor advertenties genegeerd. Stel de modus in wanneer u het `AuditudeSettings` object maakt.

1. Doorgaan met afspelen.

<!--<a id="example_6DECA71C3C3B4551805C09A80686552F"></a>-->

```java
MediaPlayer mediaPlayer =  
  new MediaPlayer(getActivity.().getApplicationContext()); 
 
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings.setSignalingMode(AdSignalingMode.MANIFEST_CUES); 
auditudeSettings.setDomain("your-auditude-domain"); 
auditudeSettings.setZoneId("your-auditude-zone-id"); 
auditudeSettings.setMediaId("your-media-id"); 
// set additional targeting parameters or custom parameters 
 
MediaPlayerItemConfig itemConfig =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
MediaResource mediaResource =  
  new MediaResource("https://example.com/media/test_media.m3u8",  
                    MediaResource.Type.HLS, Metadata); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        if (status == MediaPlayerStatus.INITIALIZED) { 
            mediaPlayer.prepareToPlay(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
            // TVSDK is in the PREPARED state, so start the playback 
            mediaPlayer.play(); 
        } 
        else if( event.getStatus() == MediaPlayerStatus.COMPLETE ) { 
            // playback has reached the end of stream ( ads included ) 
            // if we want to rewind we can call 
            mediaPlayer.seek(mediaPlayer.getSeekableRange().getBegin()); 
        } 
    } 
}); 
 
mediaPlayer.replaceCurrentResource(mediaResource, itemConfig); 
```
