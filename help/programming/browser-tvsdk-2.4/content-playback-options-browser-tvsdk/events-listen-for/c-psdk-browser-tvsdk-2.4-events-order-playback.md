---
description: Browser-TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.
title: Volgorde van afspeelgebeurtenissen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Volgorde van afspeelgebeurtenissen{#order-of-playback-events}

Browser-TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.

<!--<a id="section_D247A5873A854A079EFA6AC2E80AB894"></a>-->

In de volgende voorbeelden wordt de volgorde van bepaalde gebeurtenissen getoond, waaronder afspeelgebeurtenissen.

* Wanneer het laden van een mediabron via `replaceCurrentResource` is voltooid, is de volgorde van gebeurtenissen:

   * `AdobePSDK.MediaPlayerStatusChangeEvent` with  `event.status =`

      * `MediaPlayerStatus.INITIALIZING`
      * `MediaPlayerStatus.INITIALIZED`

* Bij het voorbereiden op afspelen via `MediaPlayer.prepareToPlay` is de volgorde van gebeurtenissen:

   * `AdobePSDK.MediaPlayerStatusChangeEvent` with  `event.status =`

      * `MediaPlayerStatus.PREPARING`
      * `MediaPlayerStatus.PREPARED`

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

In het volgende voorbeeld wordt een typische progressie van gebeurtenissen getoond:

```js
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED,  
                                 onStatusChange); 
 
onStatusChange = function (event) { 
 
    switch (event.status) { 
        case AdobePSDK.MediaPlayerStatus.IDLE: 
            console.log("Player Status: IDLE"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.INITIALIZING: 
            console.log("Player Status: INITIALIZING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            console.log("Player Status: INITIALIZED"); 
            player.prepareToPlay(); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARING: 
            console.log("Player Status: PREPARING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PREPARED: 
            console.log("Player Status: PREPARED"); 
            if (autoPlay) { 
                player.play(); 
            } 
            else { 
                dispatchEvent(ReferencePlayer.Events.PreparedEvent,  
                              {target: this}); 
            } 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PLAYING: 
            console.log("Player Status: PLAYING"); 
            //update UI play/pause to show pause icon 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.PAUSED: 
            console.log("Player Status: PAUSED"); 
            //update UI play/pause to show play icon &  
            //display pause icon over video 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.SEEKING: 
            console.log("Player Status: SEEKING"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.COMPLETE: 
            console.log("Player Status: COMPLETE"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.RELEASED: 
            console.log("Player Status: RELEASED"); 
            break; 
 
        case AdobePSDK.MediaPlayerStatus.ERROR: 
            console.log("Player Status: ERROR"); 
            break; 
    } 
};
```

