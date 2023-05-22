---
description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
title: Abonneren op aangepaste tags
exl-id: faefcefb-e52f-4e32-859a-7da4284ca52e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Abonneren op aangepaste tags {#subscribe-to-custom-tags}

TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.

Voordat het afspelen begint, moet u zich op de tags abonneren. Informatie over aangepaste tags in HLS-manifests:

1. Stel de aangepaste namen van ad-tags globaal in door een array met aangepaste tags door te geven aan `setSubscribedTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >U moet de opdracht `#` gebruiken bij het werken met HLS-streams.

   Bijvoorbeeld:

   ```java
   String[] array = new String[3]; 
   array[0] = "#EXT-X-ASSET"; 
   array[1] = "#EXT-X-BLACKOUT"; 
   array[2] = "#EXT-OATCLS-SCTE35"; 
   MediaPlayerItemConfig.setSubscribedTags(array);
   ```
