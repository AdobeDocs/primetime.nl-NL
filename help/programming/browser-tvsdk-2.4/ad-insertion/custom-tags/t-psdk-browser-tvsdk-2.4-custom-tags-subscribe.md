---
description: TimedMetadata-objecten worden door Browser-TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten worden aangetroffen in het MPD-bestand (Media Presentation Description).
title: Abonneren op aangepaste advertentietags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Abonneren op aangepaste advertentietags{#subscribe-to-custom-ad-tags}

TimedMetadata-objecten worden door Browser-TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten worden aangetroffen in het MPD-bestand (Media Presentation Description).

U moet zich op de tags abonneren voordat het afspelen begint.
Als u zich wilt abonneren op tags, stelt u een vector met de aangepaste tagnamen in op de eigenschap `subscribedTags`. Als u ook de advertentietags moet wijzigen die door de standaardopportuniteitsgenerator worden gebruikt, stelt u een vector die de aangepaste namen van ad-tags bevat in op de eigenschap `adTags`.

Abonneren op aangepaste tags:

1. Maak een nieuwe configuratie voor items in de mediaspeler.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
   ```

1. Maak een lege tekenreeksvector.

   ```js
   var subscribeTags = [];
   ```

1. Voeg de aangepaste tagnamen toe aan deze vector.

   >[!IMPORTANT]
   >
   >Als u met HLS stromen werkt, herinner me om `#` prefix te omvatten.

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Wijs de bijgewerkte vector aan het `mediaPlayerItemConfig.subscribeTags` bezit toe.

   ```js
   mediaPlayerItemConfig.subscribeTags = subscribeTags;
   ```

1. Maak een lege tekenreeksvector.

   ```js
   var adTags= [];
   ```

1. Voeg de aangepaste naam van de advertentietag toe aan deze vector.

   ```js
   adTags.push("urn:com:adobe:dpi:simple:2015");
   ```

1. Wijs de bijgewerkte vector aan het `mediaPlayerItemConfig.adTags` bezit toe.

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Gebruik de configuratie van het item voor de mediaspeler wanneer u de mediastream laadt.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```

