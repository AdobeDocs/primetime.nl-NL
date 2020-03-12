---
description: 'null'
seo-description: 'null'
seo-title: Hoofdstukondersteuning implementeren
title: Hoofdstukondersteuning implementeren
uuid: f62a8244-6393-4a38-9ae2-8ac31f6a8a06
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Hoofdstukondersteuning implementeren {#implement-chapter-support}

U kunt *aangepaste* hoofdstukken voor het bijhouden van video&#39;s definiëren en bijhouden in toepassingen die zijn gebaseerd op TVSDK.

De hoofdstukken van de douane worden beheerd door de toepassing, en zijn gebaseerd op CMS gegevens of op een andere manier die de toepassing gebruikt om hoofdstukken te bepalen.

>[!CAUTION]
>
>Standaardhoofdstukken worden niet ondersteund in de 2.5 Android-TVSDK.

1. Aangepaste hoofdstukken definiëren en bijhouden.

   ```java
   // First, enable chapter tracking by setting   
   // enableChapterTracking to true: 
   
   vaMetadata.enableChapterTracking(true); 
   // For custom chapter definitions, provide  
   // an array list of chapters through the metadata. 
   // For example: 3 chapters of 60 second duration each 
   
   List<VideoAnalyticsChapterData> chapters =  
     new ArrayList<VideoAnalyticsChapterData>(); 
   
   Int chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       VideoAnalyticsChapterData chapterData =  
         new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
       chapterData.setName("chapter_" + (i+1)); 
       chapters.add(chapterData); 
   } 
   
   vaMetadata.setChapters(chapters); 
   ```

