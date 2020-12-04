---
description: Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.
seo-description: Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.
seo-title: QoS-gebeurtenissen
title: QoS-gebeurtenissen
uuid: 3384bc51-b435-4cd9-a1f8-9abf2605205b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---


# QoS-gebeurtenissen{#qos-events}

Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.

Als u een melding wilt ontvangen over alle gebeurtenissen met betrekking tot QoS, maakt u een instantie van `AdobePSDK.QOSProvider` en koppelt u de instantie MediaPlayer aan deze instantie `QOSProvider`:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Vorm een tijdopnemer in uw toepassing om het `playbackInformation` bezit van `qosProvider` instantie periodiek te controleren. De eigenschap `playbackInformation` biedt een momentopname van de huidige afspeelstatistieken. Bijvoorbeeld:

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```

