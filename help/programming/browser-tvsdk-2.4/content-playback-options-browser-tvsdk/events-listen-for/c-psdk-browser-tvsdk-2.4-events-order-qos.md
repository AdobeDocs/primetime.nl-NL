---
description: Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.
title: QoS-gebeurtenissen
exl-id: b0fab68e-ef0f-4812-b4ad-3f69dcdf2d9e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# QoS-gebeurtenissen{#qos-events}

Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.

Om over alle op QoS betrekking hebbende gebeurtenissen op de hoogte te worden gebracht, creeer een geval van `AdobePSDK.QOSProvider` en koppel de instantie MediaPlayer aan dit `QOSProvider` instantie:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Vorm een tijdopnemer in uw toepassing periodiek om te controleren `playbackInformation` eigendom van de `qosProvider` -instantie. De `playbackInformation` eigenschap biedt een momentopname van de huidige afspeelstatistieken. Bijvoorbeeld:

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```
