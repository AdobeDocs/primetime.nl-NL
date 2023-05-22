---
description: U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.
title: Ondersteuning voor aangepaste metagegevens implementeren
exl-id: d5d8b476-0f7c-434c-9386-d060a6eb99f9
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
