---
description: U kunt de native Widevine DRM voor Android gebruiken met DASH-streams.
title: Widevine DRM
exl-id: 6a011cd7-446a-4f3a-ae36-110618001bf3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

U kunt de native Widevine DRM voor Android gebruiken met DASH-streams.

Bel het volgende `com.adobe.mediacore.drm.DRMManager` API voordat wordt begonnen met afspelen:

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

Argumenten:

* `drm` - `"com.widevine.alpha"` voor Widevine.

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
