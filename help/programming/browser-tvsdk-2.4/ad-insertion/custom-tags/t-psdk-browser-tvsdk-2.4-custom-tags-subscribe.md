---
description: TimedMetadata-objecten worden door Browser-TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten worden aangetroffen in het MPD-bestand (Media Presentation Description).
title: Abonneren op aangepaste advertentietags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Abonneren op aangepaste advertentietags{#subscribe-to-custom-ad-tags}

TimedMetadata-objecten worden door Browser-TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten worden aangetroffen in het MPD-bestand (Media Presentation Description).

U moet zich op de tags abonneren voordat het afspelen begint.
Als u zich wilt abonneren op tags, stelt u een vector met de aangepaste tagnamen in op de `subscribedTags` eigenschap. Als u ook de advertentietags moet wijzigen die door de standaardopportuniteitsgenerator worden gebruikt, stelt u een vector in die de aangepaste namen van ad-tags bevat op de `adTags` eigenschap.

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
   >Als u werkt met HLS-streams, vergeet dan niet om de `#` voorvoegsel

   ```js
   subscribeTags.push("urn:mpeg:dash:event:2012"); 
   subscribeTags.push("urn:com:adobe:dpi:simple:2015"); 
   ```

1. Wijs de bijgewerkte vector toe aan de `mediaPlayerItemConfig.subscribeTags` eigenschap.

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

1. Wijs de bijgewerkte vector toe aan de `mediaPlayerItemConfig.adTags` eigenschap.

   ```js
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Gebruik de configuratie van het item voor de mediaspeler wanneer u de mediastream laadt.

   ```js
   player.replaceCurrentResource(mediaResource,mediaPlayerItemConfig);
   ```
