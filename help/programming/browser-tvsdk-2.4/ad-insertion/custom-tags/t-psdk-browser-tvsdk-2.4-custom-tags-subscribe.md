---
description: TimedMetadata-objecten worden door Browser-TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten worden aangetroffen in het MPD-bestand (Media Presentation Description).
seo-description: TimedMetadata-objecten worden door Browser-TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten worden aangetroffen in het MPD-bestand (Media Presentation Description).
seo-title: Abonneren op aangepaste advertentietags
title: Abonneren op aangepaste advertentietags
uuid: 208f61f4-dc33-4363-aa71-878458740a8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Abonneren op aangepaste advertentietags{#subscribe-to-custom-ad-tags}

TimedMetadata-objecten worden door Browser-TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten worden aangetroffen in het MPD-bestand (Media Presentation Description).

U moet zich op de tags abonneren voordat het afspelen begint.
Als u zich wilt abonneren op tags, stelt u een vector met de aangepaste tagnamen in op de `subscribedTags` eigenschap. Als u ook de advertentietags moet wijzigen die door de standaardopportuniteitsgenerator worden gebruikt, stelt u een vector in die de aangepaste namen van ad-tags aan de `adTags` eigenschap bevat.

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
   >Als u werkt met HLS-streams, vergeet dan niet het `#` voorvoegsel op te nemen.

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

