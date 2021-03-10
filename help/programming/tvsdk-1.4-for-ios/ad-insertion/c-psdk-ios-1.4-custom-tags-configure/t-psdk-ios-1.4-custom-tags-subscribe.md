---
description: TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
title: Abonneren op aangepaste tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

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

