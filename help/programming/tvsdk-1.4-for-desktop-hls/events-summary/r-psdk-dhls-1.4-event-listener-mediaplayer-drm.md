---
description: TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen.
title: DRM-gebeurtenissen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# DRM-gebeurtenissen{#drm-events}

TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen.

Als u op de hoogte wilt worden gesteld van alle DRM-gerelateerde gebeurtenissen, luistert u naar `DRMMetadataInfoEvent` voor DRM-gebeurtenissen met de `MediaPlayer` object.

| Gebeurtenis | Betekenis |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | Er zijn nieuwe DRM-metagegevens beschikbaar. |
