---
description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
title: Gebeurtenissen van Loader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Gebeurtenissen van Loader{#loader-events}

TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.

Deze gebeurtenissen bieden een alternatieve workflow. U hoeft deze interface niet te implementeren wanneer u een MediaPlayer maakt. Gebruik deze optie als u een `MediaPlayerItemLoader`.

Registreer een implementatie van `MediaPlayerItemLoader.LoaderListener` inclusief de volgende gebeurtenissen.

| Gebeurtenis | Betekenis |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | Het laden van mediabronnen is voltooid. |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | Er is een probleem opgetreden bij het laden van mediabronnen. |

>[!NOTE]
>
>Zie ook `onLoadInfo (loadInfo)` onder QoS gebeurtenissen.
