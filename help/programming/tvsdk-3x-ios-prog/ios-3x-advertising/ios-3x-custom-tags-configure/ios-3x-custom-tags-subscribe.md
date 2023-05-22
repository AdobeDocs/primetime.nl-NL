---
description: TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
title: Abonneren op aangepaste tags
exl-id: 5074e622-8824-4253-a668-485e2f68f156
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Abonneren op aangepaste tags {#subscribe-to-custom-tags}

TvSDK bereidt PTTimedMetadata-objecten voor op geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.

Voordat het afspelen begint, moet u zich op de tags abonneren.
Informatie over aangepaste tags in HLS-manifests:

1. Stel de aangepaste namen van ad-tags globaal in door een array met aangepaste tags door te geven aan `setSubscribedTags` in `PTSDKConfig`.

   >[!IMPORTANT]
   >
   >U moet de opdracht `#` gebruiken bij het werken met HLS-streams.

   Bijvoorbeeld:

   ```
   NSArray *customHLSTags = [NSArray arrayWithObjects:@"#EXT-OATCLS-SCTE35",@"#EXT_CUSTOM_TAG2",nil]; 
   [PTSDKConfig  setSubscribedTags:customHLSTags];
   ```
