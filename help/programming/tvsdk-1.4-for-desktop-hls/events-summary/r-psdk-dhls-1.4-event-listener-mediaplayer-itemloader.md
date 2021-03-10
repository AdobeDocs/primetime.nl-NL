---
description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
title: Gebeurtenissen van Loader
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Loader-gebeurtenissen{#loader-events}

TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.

Deze gebeurtenissen bieden een alternatieve workflow. U wordt niet vereist om deze interface uit te voeren wanneer het creëren van `MediaPlayer`. Gebruik dit wanneer u `MediaPlayerItemLoader` wilt hebben.

Registreer listeners voor de volgende gebeurtenissen met het object `MediaPlayerItemLoader` om een melding te ontvangen over gebeurtenissen die betrekking hebben op het laden van een mediaspeler.

| Gebeurtenis | Betekenis |
|---|---|
| MediaPlayerItemLoader.[voltooid](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Het laden van mediabronnen is voltooid. |
| MediaPlayerItemLoader.[mislukt](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Er is een probleem opgetreden bij het laden van mediabronnen. |