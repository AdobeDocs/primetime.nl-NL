---
description: U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.
title: Ondersteuning voor aangepaste metagegevens implementeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Ondersteuning voor aangepaste metagegevens implementeren {#implement-custom-metadata-support}

U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.

Callback-functies worden aangeroepen vlak voordat de traceringsaanroep wordt gemaakt, zodat uw toepassing de metagegevens kan koppelen die specifiek zijn voor een advertentie of hoofdstuk.

1. Roep callback-functies aan voor inhoud, advertenties en hoofdstukken.

   ```
   // Video Metadata Block 
       vaTrackingMetadata.videoMetadataBlock = ^NSDictionary *() 
       { 
           return @{ 
                    @"myvideoid": @"1234", 
                    @"mysdkversion": [PTSDK apiVersion] 
                    }; 
       }; 
   
   // Ad Metadata Block invoked on every ad start 
       vaTrackingMetadata.adMetadataBlock = ^NSDictionary *(PTAd *ad) 
       { 
           return @{ 
                    @"myadid": @"ad-1234", 
                    @"myad-sdkversion": [PTSDK apiVersion] 
                    }; 
       }; 
   
   // Chapter Metadata Block invoked on every chapter start 
       vaTrackingMetadata.chapterMetadataBlock = ^NSDictionary *(PTVideoAnalyticsChapterData *chapter) 
       { 
           return @{ 
                    @"mychapterid": @"chapter-1234", 
                    @"mychapter-sdkversion": [PTSDK apiVersion] 
                    }; 
       };
   ```
