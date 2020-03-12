---
description: Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.
seo-description: Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.
seo-title: Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden
title: Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden
uuid: 0e6d2a42-37a8-477e-b925-66bbc23445c1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden {#store-timed-metadata-objects-as-they-are-dispatched}

Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.

Tijdens het parseren van inhoud, wat vóór playback gebeurt, identificeert TVSDK geabonneerde markeringen en brengt uw toepassing over deze markeringen op de hoogte. De tijd die aan elk wordt geassocieerd `TimedMetadata` is de lokale tijd op de playbackchronologie.

Uw toepassing moet de volgende taken uitvoeren:

1. Houd de huidige afspeeltijd bij.
1. Pas de huidige afspeeltijd aan de verzonden `TimedMetadata` objecten aan.

1. Gebruik de instelling `TimedMetadata` waarbij de begintijd gelijk is aan de huidige lokale afspeeltijd.

   In het volgende voorbeeld ziet u hoe u `TimedMetadata` objecten in een `ArrayList`afbeelding opslaat.

   ```java
   private List<TimedMetadata> _timedMetadataList = new ArrayList<TimedMetadata>(); 
   ... 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       ... 
       if (timedMetadata.getName().equalsIgnoreCase("#EXT-X-CUE"))  { 
           _timedMetadataList.add(timedMetadata); 
       } 
       ... 
   }
   ```

