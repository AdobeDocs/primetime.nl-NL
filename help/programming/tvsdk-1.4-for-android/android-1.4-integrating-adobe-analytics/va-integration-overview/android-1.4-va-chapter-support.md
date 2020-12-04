---
description: 'null'
seo-description: 'null'
seo-title: Hoofdstukondersteuning implementeren
title: Hoofdstukondersteuning implementeren
uuid: 5b39e494-85ad-43bb-ab56-a55797aa4ef7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Hoofdstukondersteuning {#implement-chapter-support} implementeren

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
