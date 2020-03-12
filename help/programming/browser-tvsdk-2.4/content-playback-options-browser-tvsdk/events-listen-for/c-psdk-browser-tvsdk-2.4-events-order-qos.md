---
description: Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.
seo-description: Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.
seo-title: QoS-gebeurtenissen
title: QoS-gebeurtenissen
uuid: 3384bc51-b435-4cd9-a1f8-9abf2605205b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# QoS-gebeurtenissen{#qos-events}

Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.

Om op de hoogte te worden gebracht van alle gebeurtenissen die betrekking hebben op QoS, maakt u een instantie van `AdobePSDK.QOSProvider` en koppelt u de instantie MediaPlayer aan deze `QOSProvider` instantie:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Vorm een tijdopnemer in uw toepassing om het `playbackInformation` bezit van de `qosProvider` instantie periodiek te controleren. De `playbackInformation` eigenschap biedt een momentopname van de huidige afspeelstatistieken. Bijvoorbeeld:

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```

