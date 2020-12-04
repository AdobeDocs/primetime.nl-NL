---
description: Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.
seo-description: Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.
seo-title: Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden
title: Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden
uuid: 3d0ed022-829d-474e-83a9-152caeb5b317
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden {#store-timed-metadata-objects-as-they-are-dispatched}

Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.

Tijdens het parseren van inhoud, wat vóór playback gebeurt, identificeert TVSDK geabonneerde markeringen en brengt uw toepassing over deze markeringen op de hoogte.

>[!TIP]
>
>De tijd die aan elke `TimedMetadata` wordt geassocieerd is de lokale tijd op de playbackchronologie.

U kunt als volgt getimede metagegevensobjecten opslaan terwijl ze worden verzonden:

1. Houd de huidige afspeeltijd bij.
1. Pas de huidige afspeeltijd aan de verzonden `TimedMetadata`-objecten aan.

1. Gebruik `TimedMetadata` waar de begintijd gelijk is aan de huidige lokale afspeeltijd.

   In het volgende voorbeeld wordt getoond hoe u `TimedMetadata`-objecten opslaat in een `ArrayList`.

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

