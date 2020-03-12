---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.
seo-description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.
seo-title: Een mediabron laden in de MediaPlayer
title: Een mediabron laden in de MediaPlayer
uuid: ac31ccfe-161d-41a2-9a6e-38fae11ceab5
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Een mediabron laden in de MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.

1. Stel het afspeelbare item van het `MediaPlayer` object in met de nieuwe bron die moet worden afgespeeld.

   Vervang het momenteel afspeelbare item van het bestaande `MediaPlayer` object door een bestaande `replaceCurrentResource` instantie aan te roepen `MediaResource` en door te geven.

1. Wacht tot Browser TVSDK met `AdobePSDK.MediaPlayerStatusChangeEvent` `event.status` die gelijk is aan om het even welk van het volgende verzendt:

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      Via deze gebeurtenissen wordt de toepassing door het MediaPlayer-object gewaarschuwd of de mediabron is geladen.

1. Wanneer de status van de mediaspeler verandert in `MediaPlayerStatus.INITIALIZED`, kunt u een aanroep doen `MediaPlayer.prepareToPlay`.

   De geINITIALISEERDE status geeft aan dat het medium is geladen. Het aanroepen `prepareToPlay` begint het proces van het oplossen en plaatsen van reclame, als om het even welk.
1. Wanneer Browser TVSDK de `MediaPlayerStatus.PREPARED` gebeurtenis verzendt, is de mediastream geladen (er is een MediaPlayerItem gemaakt) en is deze klaar voor afspelen.

Als een mislukking voorkomt, `MediaPlayer` schakelt aan `MediaPlayerStatus.ERROR`.

De toepassing wordt ook op de hoogte gesteld door de `MediaPlayerStatus.ERROR` gebeurtenis te verzenden.

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->


De volgende vereenvoudigde voorbeeldcode illustreert het proces om een media middel te laden:

>```js>
>player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
>                                               onStatusChange); 
> 
>
onStatusChange = function (event) { 
>       var msg = ""; 
>       switch (event.status) { 
>               case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
>                       msg = "Player Status: INITIALIZED"; 
>                       console.log(msg); 
>                       player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
>                       break; 
> 
>        
       case AdobePSDK.MediaPlayerStatus.PREPARED: 
>               // The resource is successfully loaded and available 
>               // and the MediaPlayer is ready to start the playback. 
>               // Once the resource is loaded, the MediaPlayer can 
>               // provide a reference to the current "playable item" 
>                     MediaPlayerItem playerItem = player.currentItem; 
>                     if (playerItem != null) {  
>                           // here we can look at the properties of the  
>                           // loadedstream 
>                     } 
>                     break; 
>       } 
>}
>```>


