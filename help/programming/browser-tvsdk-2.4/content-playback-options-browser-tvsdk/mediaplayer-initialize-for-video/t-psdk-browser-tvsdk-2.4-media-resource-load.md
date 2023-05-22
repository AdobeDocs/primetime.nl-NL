---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.
title: Een mediabron laden in de MediaPlayer
exl-id: b775c33e-399c-4a03-a132-407944f07706
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Een mediabron laden in de MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.

1. Stel uw `MediaPlayer` het afspeelbare item van het object met de nieuwe bron die moet worden afgespeeld.

   Bestaande vervangen `MediaPlayer` momenteel afspeelbare item van object aanroepen `replaceCurrentResource` en bestaande `MediaResource` -instantie.

1. Wachten tot TVSDK van browser wordt verzonden `AdobePSDK.MediaPlayerStatusChangeEvent` with `event.status` die gelijk is aan:

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      Via deze gebeurtenissen wordt de toepassing door het MediaPlayer-object gewaarschuwd of de mediabron is geladen.

1. Wanneer de status van de mediaspeler verandert in `MediaPlayerStatus.INITIALIZED`, kunt u `MediaPlayer.prepareToPlay`.

   De geINITIALISEERDE status geeft aan dat het medium is geladen. Aanroepen `prepareToPlay` start het proces voor het oplossen en plaatsen van reclame, indien van toepassing.
1. Wanneer Browser TVSDK het `MediaPlayerStatus.PREPARED` -gebeurtenis is geladen (er is een MediaPlayerItem gemaakt) en dat de mediastream is voorbereid voor afspelen.

Als er een fout optreedt, wordt `MediaPlayer` schakelt naar de `MediaPlayerStatus.ERROR`.

Het brengt ook uw toepassing op de hoogte door de `MediaPlayerStatus.ERROR` gebeurtenis.

><!--<a id="example_3774607C6F08473282CF0CB7F3D82373"></a>-->

De volgende vereenvoudigde voorbeeldcode illustreert het proces om een media middel te laden:

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                        onStatusChange); 
 
onStatusChange = function (event) { 
    var msg = ""; 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            msg = "Player Status: INITIALIZED"; 
            console.log(msg); 
            player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARED: 
        // The resource is successfully loaded and available 
        // and the MediaPlayer is ready to start the playback. 
        // Once the resource is loaded, the MediaPlayer can 
        // provide a reference to the current "playable item" 
           MediaPlayerItem playerItem = player.currentItem; 
           if (playerItem != null) {  
              // here we can look at the properties of the  
              // loadedstream 
           } 
           break; 
    } 
}
```
