---
description: U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.
title: Ondersteuning voor aangepaste metagegevens implementeren
exl-id: 59d56d5e-959d-4fb3-8434-55ae8219fca6
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Ondersteuning voor aangepaste metagegevens implementeren {#implement-custom-metadata-support}

U kunt douanemetagegevens op inhoud, advertenties, en hoofdstuk het volgen vraag verstrekken door callback functies te gebruiken.

Callback-functies worden aangeroepen vlak voordat de traceringsaanroep wordt gemaakt, zodat uw toepassing de metagegevens kan koppelen die specifiek zijn voor een advertentie of hoofdstuk.

Roep callback-functies aan voor inhoud, advertenties en hoofdstukken.

```java
// Video Metadata Block 
vaMetadata.setVideoMetadataBlock(new VideoAnalyticsMetadata.VideoMetadataBlock() { 
    @Override 
    public HashMap<String, String> call() { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myvideoid", "1234"); 
        result.put("mysdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Ad Metadata Block invoked on every ad start 
vaMetadata.setAdMetadataBlock(new VideoAnalyticsMetadata.AdMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(Ad ad) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myadid", "ad-1234"); 
        result.put("myad-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Chapter Metadata Block invoked on every chapter start 
vaMetadata.setChapterMetadataBlock(new VideoAnalyticsMetadata.ChapterMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(VideoAnalyticsChapterData chapter) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("mychapterid", "chapter-1234"); 
        result.put("mychapter-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
});
```
