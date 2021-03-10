---
title: Hoofdstukondersteuning implementeren
description: Hoofdstukondersteuning implementeren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%

---


# Hoofdstukondersteuning implementeren{#implement-chapter-support}

Een hoofdstuk wordt gedefinieerd als de tijd tussen elk advertentieeinde. De tijd tussen een voorrol en een onderbreking wordt bijvoorbeeld gedefinieerd als het eerste hoofdstuk. U kunt hoofdstukken voor het volgen van video in een browser op TVSDK-Gebaseerde toepassing bepalen en volgen gebruikend douanehoofdstukken. De hoofdstukken van de douane worden beheerd door de toepassing en zijn gebaseerd op CMS gegevens of een andere manier die de toepassing gebruikt om hoofdstukken te bepalen.

1. Aangepaste hoofdstukken definiëren en bijhouden.

   ```js
   vaObj.enableChapterTracking = true; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata: 
   // For example: 3 chapters of 60 second duration each 
   var chapters = []; 
   var chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       var chapterData = new AdobePSDK.VA.VideoAnalyticsChapterData("chapter_" + (i+1), i * chapterDuration, chapterDuration, (i+1)); 
       chapters.push(chapterData); 
   } 
   
   vaObj.chapters = chapters;
   ```

