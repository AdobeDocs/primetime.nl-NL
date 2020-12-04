---
description: U kunt de native Widevine DRM voor Android gebruiken met DASH-streams.
seo-description: U kunt de native Widevine DRM voor Android gebruiken met DASH-streams.
seo-title: Widevine DRM
title: Widevine DRM
uuid: ceb2f18f-9e53-47d6-9d4b-7004ac1d22c9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---


# Widevine DRM {#widevine-drm}

U kunt de native Widevine DRM voor Android gebruiken met DASH-streams.

Roep de volgende `com.adobe.mediacore.drm.DRMManager` API alvorens te beginnen speel:

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

Argumenten:

* `drm` -  `"com.widevine.alpha"` voor Widevine.

* `licenseServerURL` - De URL van de Widevine-licentieserver die licentieaanvragen ontvangt.
* `requestProperties` - Bevat extra kopballen om in het uitgaande vergunningsverzoek te omvatten.

Gebruik bijvoorbeeld de volgende code wanneer u inhoud gebruikt die is verpakt voor Expressplay DRM:

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```

