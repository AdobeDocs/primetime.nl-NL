---
description: Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.
title: Metrisch
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 5%

---


# Metrisch{#metrics}

Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.

Bijvoorbeeld:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

