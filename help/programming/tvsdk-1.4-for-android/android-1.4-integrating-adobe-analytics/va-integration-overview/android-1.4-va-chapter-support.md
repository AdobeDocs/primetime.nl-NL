---
title: Hoofdstukondersteuning implementeren
description: Hoofdstukondersteuning implementeren
copied-description: true
exl-id: f86af555-4eba-4bc8-a323-41f65f23f4cc
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Hoofdstukondersteuning implementeren {#implement-chapter-support}

U kunt hoofdstukken voor video het volgen in een op TVSDK-Gebaseerde toepassing op de volgende manieren bepalen en volgen:

* Standaardhoofdstukken, die intern door TVSDK worden beheerd.

   Een hoofdstuk wordt gedefinieerd als de tijd tussen elk advertentieeinde. De tijd tussen een voorrol en een onderbreking wordt bijvoorbeeld gedefinieerd als het eerste hoofdstuk.
* De hoofdstukken van de douane, die door de toepassing worden beheerd en op CMS gegevens of een andere manier gebaseerd zijn die de toepassing gebruikt om hoofdstukken te bepalen.

1. Definieer standaardhoofdstukken en volg deze bij.

   ```java
   // First, enable chapter tracking by setting  
   // the Boolean 'enableChapterTracking' to true: 
   
   vaMetadata.enableChapterTracking(true); 
   // For custom chapter definitions, provide an array list of chapters  
   // through the metadata. 
   // For example: 3 chapters of 60 second duration each 
   
   List<VideoAnalyticsChapterData> chapters = new ArrayList<VideoAnalyticsChapterData>(); 
   
   Int chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       VideoAnalyticsChapterData chapterData =  
         new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
       chapterData.setName("chapter_" + (i+1)); 
       chapters.add(chapterData); 
   } 
   
   vaMetadata.setChapters(chapters); 
   // For default chapters, the application must not set  
   // custom chapters on the tracking metadata 
   // and simply enable chapters to be tracked by setting  
   // the boolean value as defined above.
   ```
