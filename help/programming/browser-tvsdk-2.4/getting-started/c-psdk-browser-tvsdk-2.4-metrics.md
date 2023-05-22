---
description: Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.
title: Metrisch
exl-id: 1413ddf5-b458-4040-abf8-8d9dbd6b80e2
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
