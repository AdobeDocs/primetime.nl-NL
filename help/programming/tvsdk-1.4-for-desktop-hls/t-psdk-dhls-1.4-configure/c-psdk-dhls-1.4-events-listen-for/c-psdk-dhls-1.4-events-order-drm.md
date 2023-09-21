---
description: TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen. Uw speler kan als reactie op deze gebeurtenissen acties implementeren.
title: DRM-gebeurtenissen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# DRM-gebeurtenissen{#drm-events}

TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen. Uw speler kan als reactie op deze gebeurtenissen acties implementeren.

Luister naar het volgende als u een melding wilt ontvangen over alle DRM-gerelateerde gebeurtenissen:

```
DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE
```

In het volgende voorbeeld wordt een gemiddelde progressie getoond:

```
mediaPlayer.addEventListener(DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE,  
                             onDRMMetadataInfoAvailable);   
private function onDRMMetadataInfoAvailable(event:DRMMetadataInfoEvent){ 
    var drmMetadataInfo:DRMMetadataInfo = event.drmMetadataInfo; 
    ... 
} 
```
