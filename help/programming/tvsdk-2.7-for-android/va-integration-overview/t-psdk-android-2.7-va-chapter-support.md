---
title: Hoofdstukondersteuning implementeren
description: Hoofdstukondersteuning implementeren
copied-description: true
exl-id: 4d1b3488-88c9-49ff-9e54-f78aacdabf6e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# Hoofdstukondersteuning implementeren {#implement-chapter-support}

U kunt definiëren en bijhouden *aangepast* hoofdstukken voor het bijhouden van video&#39;s in op TVSDK gebaseerde toepassingen.

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
