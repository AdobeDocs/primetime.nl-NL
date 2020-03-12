---
description: 'null'
seo-description: 'null'
seo-title: Adverteren toevoegen
title: Adverteren toevoegen
uuid: 7762506f-b55e-445d-b8a2-c1208358a370
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Adverteren toevoegen {#add-advertising}

1. De metagegevens voor advertenties definiëren.

   ```js
   var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
     auditudeSettings.domain = "auditude.com"; 
     auditudeSettings.mediaId = "adbe_tearsofsteel2"; 
     auditudeSettings.zoneId = "123869";
   ```

1. Voeg de advertentiemetagegevens aan toe `MediaResource`.

   ```js
   var mediaResource =  
     new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
   ```

1. Voeg de montages aan config toe en voeg een `SpliceOut` parseringsfabriek toe.

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings; 
   config.advertisingFactory = new ExtCueOutContentFactory(auditudeSettings);
   ```

1. Voeg het `ExtCueOutContentFactory` aan de bibliotheeksectie toe.
1. Download het bestand `ExtCueOutContentFactory.js` uit de bibliotheeksectie en plaats het in de werkmap.

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script> 
   <script src= "ExtCueOutContentFactory.js"></script>
   ```

1. Test uw configuratie.
