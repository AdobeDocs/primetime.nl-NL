---
description: Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.
seo-description: Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.
seo-title: Metrisch
title: Metrisch
uuid: 4734e532-1f83-4691-b1bd-785f78e55d8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Metrisch{#metrics}

Browser TVSDK verstrekt metriek voor het analyseren en het zuiveren te gebruiken. U kunt deze metriek krijgen door QoSProvider te gebruiken.

Bijvoorbeeld:

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

