---
description: Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.
title: Metrisch
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# Metrisch{#metrics}

Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.

Bijvoorbeeld:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```
