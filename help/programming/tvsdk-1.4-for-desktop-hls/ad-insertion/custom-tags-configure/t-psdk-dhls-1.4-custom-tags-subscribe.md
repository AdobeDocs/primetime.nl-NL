---
description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
title: Abonneren op aangepaste tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Abonneren op aangepaste tags{#subscribe-to-custom-tags}

TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.

Voordat het afspelen begint, moet u zich op de tags abonneren.
Als u zich wilt abonneren op tags, wijst u een vector met de aangepaste tagnamen toe aan de eigenschap `subscribedTags`. Als u ook de advertentietags moet wijzigen die door de standaardopportuniteitsgenerator worden gebruikt, wijst u een vector die de aangepaste namen van ad-tags bevat, toe aan de eigenschap `adTags`.

Informatie over aangepaste tags in HLS-manifests:

1. Stel de namen van aangepaste ad-tags globaal in door een vector met aangepaste tags toe te wijzen aan `subscribeTags` in `MediaPlayerItemConfig`.

   >[!IMPORTANT]
   >
   >Wanneer u met HLS-streams werkt, moet u het voorvoegsel `#` opnemen.

   Bijvoorbeeld:

   ```
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   PSDKConfig.subscribedTags = subscribedTags;
   ```

1. Als u de advertentietags die door de standaardopportuniteitsgenerator worden gebruikt, wilt wijzigen, wijst u een vector met de aangepaste namen van ad-tags toe aan de eigenschap `adTags` in `PSDKConfig`.

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   PSDKConfig.adTags = adTags; 
   ```

1. Vervang de huidige bron om alle algemene instellingen van kracht te laten worden.

   ```
   player.replaceCurrentResource(mediaResource);
   ```

1. U kunt indien nodig de geabonneerde tagnamen voor een stream instellen:
   1. Maak een mediaspeler-itemconfiguratie.

      >[!TIP]
      >
      >De eenvoudigste manier is om een standaardconfiguratie voor mediaspelers te maken.

   1. Wijs een vector toe die de douanetags aan `subscribeTags` in `MediaPlayerItemConfig` bevat.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     new DefaultMediaPlayerItemConfig(); 
   
   var subscribedTags:Vector.<String> = new Vector.<String>(); 
   subscribedTags.push("#EXT-X-ASSET"); 
   subscribedTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.subscribeTags = subscribedTags;
   ```

1. Als u de advertentietags wilt wijzigen die door de standaardopportuniteitsgenerator in de opgegeven stream worden gebruikt, wijst u een vector die de aangepaste namen van ad-tags bevat, toe aan de eigenschap `adTags` in `mediaPlayerItemConfig`

   ```
   var adTags:Vector.<String> = new Vector.<String>(); 
   adTags.push("#EXT-X-AD"); 
   mediaPlayerItemConfig.adTags = adTags;
   ```

1. Wanneer u wilt dat de wijzigingen voor de stream van kracht worden en de mediastream laadt, gebruikt u de configuratie van het item voor de mediaspeler.

   ```
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

