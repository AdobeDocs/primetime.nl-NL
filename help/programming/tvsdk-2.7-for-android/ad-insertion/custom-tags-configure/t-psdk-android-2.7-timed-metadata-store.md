---
description: Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.
title: Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden
exl-id: da7ee636-f3ac-4aac-9ca0-7075b8c910f0
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden {#store-timed-metadata-objects-as-they-are-dispatched}

Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.

Tijdens het parseren van inhoud, wat vóór playback gebeurt, identificeert TVSDK geabonneerde markeringen en brengt uw toepassing over deze markeringen op de hoogte.

>[!TIP]
>
>De tijd die aan elk wordt geassocieerd `TimedMetadata` Dit is de lokale tijd op de afspeeltijdlijn.

U kunt als volgt getimede metagegevensobjecten opslaan terwijl ze worden verzonden:

1. Houd de huidige afspeeltijd bij.
1. De huidige afspeeltijd afstemmen op de verzonden tijd `TimedMetadata` objecten.

1. Gebruik de `TimedMetadata` waarbij de begintijd gelijk is aan de huidige lokale afspeeltijd.

   In het volgende voorbeeld wordt getoond hoe u het bestand opslaat `TimedMetadata` objecten in een `ArrayList`.

   ```java
   private List<TimedMetadata> _timedMetadataList =  
     new ArrayList<TimedMetadata>(); 
   ... 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       ... 
       if (timedMetadata.getName().equalsIgnoreCase("#EXT-X-CUE"))  { 
           _timedMetadataList.add(timedMetadata); 
       } 
       ... 
   }
   ```
