---
description: TVSDK verzendt de gebeurtenissen met betrekking tot media Player-items als reactie op het laden van een media-item.
title: Gebeurtenissen van Loader
exl-id: 80a503f2-ad2e-44e5-93dc-2311df77f52e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
