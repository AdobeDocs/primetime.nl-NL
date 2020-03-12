---
description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
seo-description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
seo-title: Gebeurtenissen van Loader
title: Gebeurtenissen van Loader
uuid: 1b401ff5-4313-4c64-8be9-99bdeb58ba2a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Gebeurtenissen van Loader{#loader-events}

TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.

Deze gebeurtenissen bieden een alternatieve workflow. U hoeft deze interface niet te implementeren wanneer u een MediaPlayer maakt. Gebruik dit wanneer u een `MediaPlayerItemLoader`wilt hebben.

Registreer een implementatie van de volgende gebeurtenissen om op de hoogte te worden gebracht van gebeurtenissen die te maken hebben met het laden van een mediaspeler. `MediaPlayerItemLoader.LoaderListener` Dit geldt ook voor de volgende gebeurtenissen.

| Gebeurtenis | Betekenis |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | Het laden van mediabronnen is voltooid. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Er is een probleem opgetreden bij het laden van mediabronnen. |

>[!NOTE]
>
>Zie ook `onLoadInfo (loadInfo)` onder gebeurtenissen QoS.

