---
description: TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-description: TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-title: Abonneren op aangepaste tags
title: Abonneren op aangepaste tags
uuid: de66d3db-46d1-485f-9d3a-6e28495bfb13
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 1%

---


# Abonneren op aangepaste tags {#subscribe-to-custom-tags}

TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.

Voordat het afspelen begint, moet u zich op de tags abonneren.
Informatie over aangepaste tags in HLS-manifests:

1. Stel de namen van aangepaste ad-tags globaal in door een array met aangepaste tags door te geven aan `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >Wanneer u met HLS-streams werkt, moet u het voorvoegsel `#` opnemen.

   Bijvoorbeeld:

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```

