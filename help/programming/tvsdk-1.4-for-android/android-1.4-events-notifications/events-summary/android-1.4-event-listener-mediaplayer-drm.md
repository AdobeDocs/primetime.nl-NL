---
description: TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen.
title: DRM-gebeurtenissen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# DRM-gebeurtenissen{#drm-events}

TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen.

Registreer een implementatie van `MediaPlayer.DRMEventListener` die de volgende callback bevat om op de hoogte te worden gebracht van alle DRM-gerelateerde gebeurtenissen.

| Gebeurtenis | Betekenis |
|---|---|
| [onDRMMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.DRMEventListener.html#onDRMMetadata(DRMMetadataInfo)) `(DRMMetadataInfo drmMetadataInfo)` | Er zijn nieuwe DRM-metagegevens beschikbaar. |

