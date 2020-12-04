---
description: 'null'
seo-description: 'null'
seo-title: Hoofdstukondersteuning implementeren
title: Hoofdstukondersteuning implementeren
uuid: 4224cd2e-1e16-4040-972b-92c91506408f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Hoofdstukondersteuning implementeren{#implement-chapter-support}

U kunt hoofdstukken voor video het volgen in een op TVSDK-Gebaseerde toepassing op de volgende manieren bepalen en volgen:

* Standaardhoofdstukken, die intern door TVSDK worden beheerd.

   Een hoofdstuk wordt gedefinieerd als de tijd tussen elk advertentieeinde. De tijd tussen een voorrol en een onderbreking wordt bijvoorbeeld gedefinieerd als het eerste hoofdstuk.
* De hoofdstukken van de douane, die door de toepassing worden beheerd en op CMS gegevens of een andere manier gebaseerd zijn die de toepassing gebruikt om hoofdstukken te bepalen.

   Definieer standaardhoofdstukken en volg deze bij.

   ```
   // First, enable chapter tracking by setting the boolean 'enableChapterTracking' to true: 
   
       vaTrackingMetadata.enableChapterTracking = YES; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata:  
   // For example, 3 chapters of 60 second duration each: 
   
       NSMutableArray *chapters = [[[NSMutableArray alloc] init] autorelease]; 
   
       int chapterDuration = 60; 
       for (int i = 0; i < 3; i++) 
       { 
           PTVideoAnalyticsChapterData *chapterData =  
             [[[PTVideoAnalyticsChapterData alloc] init] autorelease]; 
           chapterData.name = [NSString stringWithFormat:@"chapter_%d", (i+1)]; 
           chapterData.range =  
             CMTimeRangeMake(CMTimeMakeWithSeconds(i * chapterDuration, 10000),  
             CMTimeMakeWithSeconds(chapterDuration, 10000)); 
   
           [chapters addObject:chapterData]; 
       } 
   
       vaTrackingMetadata.chapters = chapters; 
   
   // For default chapters, the application must not set custom chapters on the tracking metadata  
   // and simply enable chapters to be tracked by setting the boolean value as defined above.
   ```

