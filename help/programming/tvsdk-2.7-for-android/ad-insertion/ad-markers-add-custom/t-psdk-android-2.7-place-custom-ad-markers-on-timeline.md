---
description: In dit voorbeeld ziet u de aanbevolen manier om aangepaste en markeertekens op de afspeeltijdlijn op te nemen.
title: Aangepaste markeertekens op de tijdlijn plaatsen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Aangepaste markeertekens op de tijdlijn plaatsen {#place-custom-ad-markers-on-the-timeline}

In dit voorbeeld ziet u de aanbevolen manier om aangepaste en markeertekens op de afspeeltijdlijn op te nemen.

1. Vertaal de out-of-band ad-positioneringsinformatie in een lijst/serie van `RepaceTimeRange` klasse.
1. Een instantie maken van `CustomRangeMetadata` klasse, en gebruik zijn `setTimeRangeList` methode met de lijst/array als argument om de lijst met tijdbereiken in te stellen.
1. Gebruik het `setType` methode om het type in te stellen op `MARK_RANGE`.
1. Gebruik de `MediaPlayerItemConfig.setCustomRangeMetadata` met de `CustomRangeMetadata` instantie als argument om de metagegevens van het aangepaste bereik in te stellen.
1. Gebruik de `MediaPlayer.replaceCurrentResource` met de `MediaPlayerItemConfig` instantie als argument om in te stellen, de nieuwe bron de huidige.
1. Wacht op een `STATE_CHANGED` gebeurtenis, die aangeeft dat de speler zich in de `PREPARED` status.
1. Video afspelen starten door `MediaPlayer.play`.

Hier volgt het resultaat van het voltooien van de taken in dit voorbeeld: >
* Indien een `ReplaceTimeRange` overlapt een andere gebeurtenis op de afspeeltijdlijn, bijvoorbeeld de beginpositie van een `ReplaceTimeRange` eerder is dan een reeds geplaatste eindpositie, wordt het begin van de overtreding stilletjes aangepast door TVSDK `ReplaceTimeRange` om het conflict te voorkomen.

  Hierdoor wordt de aangepaste `ReplaceTimeRange` korter dan oorspronkelijk opgegeven. Als de aanpassing tot een duur van nul leidt, laat TVSDK de overtreding stil vallen `ReplaceTimeRange`.

* TVSDK zoekt naar aangrenzende tijdbereiken voor aangepaste en afbrekingen en voegt deze in afzonderlijke ad-einden samen.

  Tijdbereiken die zich niet naast een ander tijdbereik bevinden, worden omgezet in ad-hocafbrekingen die één advertentie bevatten.
* Als de toepassing een mediabrondel probeert te laden waarvan de configuratie `CustomRangeMetadata` die alleen in de context van aangepaste advertentiemarkeringen kunnen worden gebruikt, genereert TVSDK een uitzondering als het onderliggende actief niet van het type VOD is.
* Bij het omgaan met aangepaste advertentiemarkeringen deactiveert TVSDK andere ad-resolving mechanismen (bijvoorbeeld Adobe Primetime en besluitvorming).

  U kunt elke TVSDK-ad-resolver-module of het aangepaste ad-markeermechanisme gebruiken. Wanneer u aangepaste advertentiemarkeringen gebruikt, wordt de advertentie-inhoud beschouwd als zijnde opgelost en op de tijdlijn geplaatst.

In het volgende codefragment worden drie tijdbereiken op de tijdlijn geplaatst als aangepaste advertentiemarkeringen.

```java
// Assume that the 3 time ranges are obtained through external means 
// Use them to populate the ReplaceTimeRange instance 
List<ReplaceTimeRange> timeRanges = new ArrayList<ReplaceTimeRange>(); 
timeRanges.add(new ReplaceTimeRange(0,10000, 0)); 
timeRanges.add(new ReplaceTimeRange(15000,20000, 0)); 
timeRanges.add(new ReplaceTimeRange(25000,30000, 0)); 
 
CustomRangeMetadata customRangeMetadata = new CustomRangeMetadata(); 
customRangeMetadata.setTimeRangeList(timeRanges); 
customRangeMetadata.setType(CustomRangeMetadata.CustomRangeType.MARK_RANGE); 
 
//Create a MediaResource instance 
MediaResource mediaResource = MediaResource.createFromUrl( 
        "www.example.com/video/test_video.m3u8", timeRanges.toMedatada(null)); 
 
// Create a MediaPlayerItemConfig instance 
MediaPlayerItemConfig config =  
  new MediaPlayerItemConfig(getActivity().getApplicationContext()); 
 
// Set customRangeMetadata 
config.setCustomRangeMetadata(customRangeMetadata); 
 
// Prepare the content for playback by calling replaceCurrentResource 
// NOTE: mediaPlayer is an instance of a properly configured MediaPlayer  
mediaPlayer.replaceCurrentResource(mediaResource, config); 
 
// wait for TVSDK to reach the PREPARED state 
mediaPlayer.addEventListener(MediaPlayerEvent.STATE_CHANGED,  
  new StatusChangeEventListener() { 
    @Override 
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
 
    if( event.getStatus() == MediaPlayerStatus.PREPARED ) { 
        // TVSDK is in the PREPARED state, so start the playback  
        mediaPlayer.play(); 
    } 
    ... 
}
```
