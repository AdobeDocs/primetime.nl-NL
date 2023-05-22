---
description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
title: Gebeurtenissen van Loader
exl-id: ee5be2d4-5c77-4af4-b8fe-8cef18d7c0d9
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
