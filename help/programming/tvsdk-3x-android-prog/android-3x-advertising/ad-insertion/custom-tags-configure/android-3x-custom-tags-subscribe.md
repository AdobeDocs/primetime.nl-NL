---
description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-title: Abonneren op aangepaste tags
title: Abonneren op aangepaste tags
uuid: f1a934bd-772e-435f-84b5-cb48db23c06e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
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
