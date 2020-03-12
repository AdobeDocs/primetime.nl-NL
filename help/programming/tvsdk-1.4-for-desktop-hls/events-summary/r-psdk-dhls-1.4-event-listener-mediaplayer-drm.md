---
description: TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen.
seo-description: TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen.
seo-title: DRM-gebeurtenissen
title: DRM-gebeurtenissen
uuid: f1da5b31-3fad-4bb4-8aa3-3925d5f0e123
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# DRM-gebeurtenissen{#drm-events}

TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen.

Luister naar DRM-gebeurtenissen met het `DRMMetadataInfoEvent` `MediaPlayer` object als u een melding wilt ontvangen over alle DRM-gerelateerde gebeurtenissen.

| Gebeurtenis | Betekenis |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | Er zijn nieuwe DRM-metagegevens beschikbaar. |