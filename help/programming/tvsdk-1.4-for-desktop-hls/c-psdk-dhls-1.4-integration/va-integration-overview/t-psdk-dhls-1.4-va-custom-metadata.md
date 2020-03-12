---
description: U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.
seo-description: U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.
seo-title: Ondersteuning voor aangepaste metagegevens implementeren
title: Ondersteuning voor aangepaste metagegevens implementeren
uuid: 2186db58-10b0-43a6-840f-53ab289843ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ondersteuning voor aangepaste metagegevens implementeren{#implement-custom-metadata-support}

U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.

Callback-functies worden aangeroepen vlak voordat de traceringsaanroep wordt gemaakt, zodat uw toepassing de metagegevens kan koppelen die specifiek zijn voor een advertentie of hoofdstuk.

1. Roep callback-functies aan voor inhoud, advertenties en hoofdstukken.

   ```
   // Video Metadata Block 
   vaMetadata.videoMetadataBlock = function():Object { 
       return {"myvideoid":"1234", "mysdkversion":Version.version} 
   }; 
   
   // Ad Metadata Block invoked on every ad start 
   vaMetadata.adMetadataBlock = function(ad:Ad):Object { 
       return {"myadid":"ad-1234", "myad-sdkversion":Version.version} 
   }; 
   
   // Chapter Metadata Block invoked on every chapter start 
   vaMetadata.chapterMetadataBlock = function(chapter:VideoAnalyticsChapterData) { 
       return {"mychapterid":"chapter-1234", "mychapter-sdkversion":Version.version} 
   };
   ```

