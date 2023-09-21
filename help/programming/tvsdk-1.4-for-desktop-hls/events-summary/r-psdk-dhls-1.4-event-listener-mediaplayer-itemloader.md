---
description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
title: Gebeurtenissen van Loader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Gebeurtenissen van Loader{#loader-events}

TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.

Deze gebeurtenissen bieden een alternatieve workflow. U hoeft deze interface niet te implementeren wanneer u een `MediaPlayer`. Gebruik deze optie als u een `MediaPlayerItemLoader`.

Registreer listeners voor de volgende gebeurtenissen bij de `MediaPlayerItemLoader` object.

| Gebeurtenis | Betekenis |
|---|---|
| MediaPlayerItemLoader.[voltooid](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Het laden van mediabronnen is voltooid. |
| MediaPlayerItemLoader.[mislukt](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Er is een probleem opgetreden bij het laden van mediabronnen. |
