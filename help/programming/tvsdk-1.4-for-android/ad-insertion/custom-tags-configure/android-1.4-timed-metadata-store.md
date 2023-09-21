---
description: Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.
title: Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Metagegevensobjecten met tijdslimiet opslaan terwijl ze worden verzonden {#store-timed-metadata-objects-as-they-are-dispatched}

Uw toepassing moet de juiste TimedMetadata-objecten op de juiste momenten gebruiken.

Tijdens het parseren van inhoud, wat vóór playback gebeurt, identificeert TVSDK geabonneerde markeringen en brengt uw toepassing over deze markeringen op de hoogte. De tijd die aan elk wordt geassocieerd `TimedMetadata` Dit is de lokale tijd op de afspeeltijdlijn.

Uw toepassing moet de volgende taken uitvoeren:

1. Houd de huidige afspeeltijd bij.
1. Pas de huidige afspeeltijd aan de verzonden `TimedMetadata` objecten.

1. Gebruik de `TimedMetadata` waarbij de begintijd gelijk is aan de huidige lokale afspeeltijd.

   In het volgende voorbeeld wordt getoond hoe u het bestand opslaat `TimedMetadata` objecten in een `ArrayList`.

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
