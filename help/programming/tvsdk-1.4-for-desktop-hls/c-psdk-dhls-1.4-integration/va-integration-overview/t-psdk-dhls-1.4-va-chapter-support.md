---
title: Hoofdstukondersteuning implementeren
description: Hoofdstukondersteuning implementeren
copied-description: true
exl-id: c6d9300e-33ce-4948-af5b-f28945fd47e4
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

   Definieer standaardhoofdstukken en volg deze bij.

   ```
   // First, enable chapter tracking by setting the boolean 'enableChapterTracking' to true: 
   
       vaMetadata.enableChapterTracking = true; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata:  
   // For example: 3 chapters of 60 second duration each 
   
       var chapters:Vector.<VideoAnalyticsChapterData> = new Vector.<VideoAnalyticsChapterData>(); 
       var chapterDuration:int = 60; 
       for (var i:int = 0; i < 3; i++) { 
           var chapterData:VideoAnalyticsChapterData =  
             new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration); 
           chapterData.name = "chapter_%d" + (i+1); 
   
           chapters.push(chapterData); 
       } 
   
       vaMetadata.chapters = chapters; 
   
   // For default chapters, the application must not set custom chapters on the tracking metadata  
   // and simply enable chapters to be tracked by setting the boolean value as defined above. 
   ```
