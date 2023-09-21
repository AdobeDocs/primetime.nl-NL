---
description: Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.
title: QoS-gebeurtenissen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# QoS-gebeurtenissen{#qos-events}

Browser TVSDK verzendt de kwaliteit van de dienst (QoS) gebeurtenissen om uw toepassing over gebeurtenissen op de hoogte te brengen die de berekening van statistieken QoS, zoals het bufferen en het zoeken gebeurtenissen konden beïnvloeden.

Maak een instantie van `AdobePSDK.QOSProvider` en koppel de instantie MediaPlayer aan dit `QOSProvider` -instantie:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
// initialize QOS provider before setting media  
qosProvider.attachMediaPlayer(player);
```

Configureer een timer in uw toepassing om de `playbackInformation` eigendom van de `qosProvider` -instantie. De `playbackInformation` eigenschap biedt een momentopname van de huidige afspeelstatistieken. Bijvoorbeeld:

```js
var startTimer = function () { 
   var metrics = qosProvider.playbackInformation; 
 
    //analyze metrics 
    //for e.g. metrics.timeToFirstByte ; metrics.timeToLoad etc.  
    //refer API doc for supported metrics  
} 
window.setTimeout(startTimer, 500) 
```
