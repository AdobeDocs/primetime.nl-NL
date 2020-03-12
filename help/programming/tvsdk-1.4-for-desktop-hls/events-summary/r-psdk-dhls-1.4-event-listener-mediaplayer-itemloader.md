---
description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
seo-description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
seo-title: Gebeurtenissen van Loader
title: Gebeurtenissen van Loader
uuid: 0ad37715-14b1-457c-892f-0db0d6220f0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Gebeurtenissen van Loader{#loader-events}

TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.

Deze gebeurtenissen bieden een alternatieve workflow. U wordt niet vereist om deze interface uit te voeren wanneer het creëren van een `MediaPlayer`. Gebruik dit wanneer u een `MediaPlayerItemLoader`wilt hebben.

Registreer listeners voor de volgende gebeurtenissen bij het `MediaPlayerItemLoader` object om een melding te ontvangen over gebeurtenissen die betrekking hebben op het laden van een mediaspeler.

| Gebeurtenis | Betekenis |
|---|---|
| MediaPlayerItemLoader.[voltooid](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | Het laden van mediabronnen is voltooid. |
| MediaPlayerItemLoader.[mislukt](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | Er is een probleem opgetreden bij het laden van mediabronnen. |