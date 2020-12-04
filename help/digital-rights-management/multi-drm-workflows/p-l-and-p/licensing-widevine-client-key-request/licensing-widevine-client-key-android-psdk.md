---
description: De clientcode geeft gegevens door aan een Android-API.
seo-description: De clientcode geeft gegevens door aan een Android-API.
seo-title: Belangrijke aanvraagworkflow voor Android PSDK
title: Belangrijke aanvraagworkflow voor Android PSDK
uuid: 575163de-0f96-434d-a3ff-7e114caf72de
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Belangrijke aanvraagworkflow voor Android PSDK{#key-request-workflow-on-android-psdk}

De clientcode geeft gegevens door aan een Android-API.

Op Android moet uw clientcode de URL van de licentieserver en de bijbehorende gegevens voor licentieaanschaf doorgeven met behulp van de volgende API:

```
class DRMManager 
   { 
   ... 
   /* 
   * Set the license server URL and attached request properties that the PSDK should use for the passed in drm type.  
   * 
   * drmType: "com.widevine.alpha" for widevine. "com.microsoft.playready" for playready. 
   * licenseServerURL: self explanatory.  
   * requestProperties: key value pairs to be attached as HTTP headers to all license request sent to the passed in license server URL. Pass in 
   * NULL if none is needed.  
   */ 
   public static void setProtectionData(String drmType, String licenseServerURL,  Map<String, String> requestProperties); 
    }
```

Nadat deze API met succes is aangeroepen, kan uw code het afspelen van inhoud op de gebruikelijke manier starten. Als u Expressplay gebruikt, kunt u of het teken als deel van de vergunningsserver URL of als verzoekbezit overgaan en uit het teken van de vergunningsserver URL schrappen.

Sommige Android-apparaten ondersteunen zowel Windows als PlayReady. Op dergelijke apparaten kan de klant PSDK dwingen de inhoud te decoderen gebruikend bepaalde DRM als de inhoud veelvoudige DRM kopballen heeft. Dit kan door volgende API vóór playback te roepen:

```
class MediaPlayer 
   { 
   ... 
    
   /* 
   * drm: pass in "com.widevine.alpha" for widevine or "com.microsoft.playready" for playready 
   * 
   */ 
   public void setDRMScheme(String drm) throws MediaPlayerException 
   }
```

