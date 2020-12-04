---
description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.
seo-description: Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.
seo-title: Een mediabron laden in de MediaPlayer
title: Een mediabron laden in de MediaPlayer
uuid: ac31ccfe-161d-41a2-9a6e-38fae11ceab5
translation-type: tm+mt
source-git-commit: 7d61a6cd8cb2c381f85a19d9ccac3d235ffceaf1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Een mediabron laden in de MediaPlayer {#load-a-media-resource-in-the-mediaplayer}

Laad een bron door rechtstreeks een MediaResource te instantiëren en de video-inhoud te laden die moet worden afgespeeld.

1. Stel het afspeelbare item van het `MediaPlayer`-object in met de nieuwe bron die moet worden afgespeeld.

   Vervang het huidige afspeelbare item van het `MediaPlayer`-object door `replaceCurrentResource` aan te roepen en een bestaande `MediaResource`-instantie door te geven.

1. Wacht tot Browser TVSDK `AdobePSDK.MediaPlayerStatusChangeEvent` met `event.status` verzendt die aan om het even welk van het volgende gelijk is:

   * `MediaPlayerStatus.INITIALIZED`
   * `MediaPlayerStatus.PREPARED`
   * `MediaPlayerStatus.ERROR`

      Via deze gebeurtenissen wordt de toepassing door het MediaPlayer-object gewaarschuwd of de mediabron is geladen.

1. Wanneer de status van de mediaspeler verandert in `MediaPlayerStatus.INITIALIZED`, kunt u `MediaPlayer.prepareToPlay` aanroepen.

   De geINITIALISEERDE status geeft aan dat het medium is geladen. Als u `prepareToPlay` aanroept, wordt het proces voor het oplossen en plaatsen van advertenties gestart, indien van toepassing.
1. Wanneer Browser TVSDK de gebeurtenis `MediaPlayerStatus.PREPARED` verzendt, is de mediastream geladen (er is een MediaPlayerItem gemaakt) en is deze klaar voor afspelen.

Als er een fout optreedt, schakelt `MediaPlayer` over naar `MediaPlayerStatus.ERROR`.

Het brengt ook uw toepassing op de hoogte door de gebeurtenis `MediaPlayerStatus.ERROR` te verzenden.

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
