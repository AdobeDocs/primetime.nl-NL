---
description: 'null'
seo-description: 'null'
seo-title: Hoofdstukondersteuning implementeren
title: Hoofdstukondersteuning implementeren
uuid: 6e2c3994-d28b-489f-ae60-9b876125a871
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# Hoofdstukondersteuning {#implement-chapter-support} implementeren

U kunt *aangepaste* hoofdstukken definiëren en bijhouden voor videotracering in toepassingen die zijn gebaseerd op TVSDK.

De hoofdstukken van de douane worden beheerd door de toepassing, en zijn gebaseerd op CMS gegevens of op een andere manier die de toepassing gebruikt om hoofdstukken te bepalen.

>[!CAUTION]
>
>Standaardhoofdstukken worden niet ondersteund in de 3.0 Android-TVSDK.

Aangepaste hoofdstukken definiëren en bijhouden.

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
