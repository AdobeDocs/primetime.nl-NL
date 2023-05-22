---
title: Adverteren toevoegen
description: Adverteren toevoegen
copied-description: true
exl-id: 72f875ea-80ae-482b-94be-41116fff3614
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Adverteren toevoegen {#add-advertising}

1. De metagegevens voor advertenties definiëren.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. Voeg de advertentiemetagegevens toe aan de `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. Voeg de montages aan config toe en voeg a toe `SpliceOut` parseringsfabriek.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. Voeg de `ExtCueOutContentFactory` naar de bibliotheeksectie.
1. Download de `ExtCueOutContentFactory.js` in de bibliotheeksectie en plaats deze in de werkmap.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Test uw configuratie.
