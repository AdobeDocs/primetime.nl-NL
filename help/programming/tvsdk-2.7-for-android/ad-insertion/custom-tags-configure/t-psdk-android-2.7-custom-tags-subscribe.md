---
description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-title: Abonneren op aangepaste tags
title: Abonneren op aangepaste tags
uuid: 9f74b2b9-bbc9-433c-8226-2c2b68eddf7e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 1%

---


# Abonneren op aangepaste tags {#subscribe-to-custom-tags}

TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.

Voordat het afspelen begint, moet u zich op de tags abonneren. Informatie over aangepaste tags in HLS-manifests:

1. Stel de namen van aangepaste ad-tags globaal in door een array met aangepaste tags door te geven aan `setSubscribedTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Wanneer u met HLS-streams werkt, moet u het voorvoegsel `#` opnemen.

   Bijvoorbeeld:

   ```java
   String[] array = new String[3]; 
   array[0] = "#EXT-X-ASSET"; 
   array[1] = "#EXT-X-BLACKOUT"; 
   array[2] = "#EXT-OATCLS-SCTE35"; 
   MediaPlayerItemConfig.setSubscribedTags(array);
   ```

