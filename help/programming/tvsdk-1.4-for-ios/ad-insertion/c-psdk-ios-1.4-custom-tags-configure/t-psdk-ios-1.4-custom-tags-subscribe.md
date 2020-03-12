---
description: TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-description: TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-title: Abonneren op aangepaste tags
title: Abonneren op aangepaste tags
uuid: de66d3db-46d1-485f-9d3a-6e28495bfb13
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Abonneren op aangepaste tags {#subscribe-to-custom-tags}

TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.

Voordat het afspelen begint, moet u zich op de tags abonneren.
Informatie over aangepaste tags in HLS-manifests:

1. Stel de aangepaste namen van tags globaal in door een array met aangepaste tags door te geven `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >U moet het `#` voorvoegsel opnemen wanneer u werkt met HLS-streams.

   Bijvoorbeeld:

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```

