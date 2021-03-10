---
description: U kunt Digital Rights Management-specifieke workflows (DRM) voltooien.
title: Digital Rights Management
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Digital Rights Management {#digital-rights-management}

U kunt Digital Rights Management-specifieke workflows (DRM) voltooien.

U kunt naar de gebeurtenis `AdobePSDK.DRMMetadataInfoEvent` luisteren om DRM-workflows te verwerken:

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## Digital Rights Management {#add-digital-rights-management} toevoegen

1. Voeg `DRMMetadataInfoAvailableEvent` toe om `DRMMetadata` te krijgen.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. Implementeer de sectie `onDRMMetadataInfoAvailable` boven de regel in stap 1.

   ```js
   var onDRMMetadataInfoAvaialble = function(event) { 
    var drmMetadataInfo = event.drmMetadataInfo; 
    var drmMetadata = null; 
   
    if(drmMetadataInfo) { 
     drmMetadata = drmMetadataInfo.drmMetadata; 
    } 
   
    drmManager.acquireLicense(drmMetadata, null, null); 
   };
   ```

1. Maak de DRMManager in de methode setupVideo.

   ```js
   var drmManager = player.drmManager;
   ```

1. Maak de beveiligingsgegevens voor Windows en PlayReady door het volgende voorbeeld te kopiëren:

   ```js
   var protectionData = { 
     "com.widevine.alpha":{ 
       "serverURL":"https://wv.service.expressplay.com/hms/wv/rights/? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]"  
     }, 
   
     "com.microsoft.playready":{ 
       "serverURL":"https://pr.test.expressplay.com/playready/RightsManager.asmx? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]", 
         "httpRequestHeaders":{ 
       } 
     } 
   };
   ```

1. Voeg de beveiligingsgegevens toe aan drmManager.

   ```js
   drmManager.setProtectionData(protectionData);
   ```

1. Wijzig de bron-URL in een DASH-teststream.

   >[!TIP]
   >
   >Zorg ervoor dat u het middeltype bijwerkt, omdat dit nu DASH is.

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. Test uw configuratie.