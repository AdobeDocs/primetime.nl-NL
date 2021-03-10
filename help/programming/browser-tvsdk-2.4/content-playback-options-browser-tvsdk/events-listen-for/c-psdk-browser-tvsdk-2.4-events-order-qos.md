---
description: Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.
title: QoS-gebeurtenissen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
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

