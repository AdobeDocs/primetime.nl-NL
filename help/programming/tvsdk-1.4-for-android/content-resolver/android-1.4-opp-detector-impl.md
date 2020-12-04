---
description: U kunt uw eigen opportuniteitsdetectors implementeren door de interface PlacementOpportunityDetector te implementeren.
seo-description: U kunt uw eigen opportuniteitsdetectors implementeren door de interface PlacementOpportunityDetector te implementeren.
seo-title: Een aangepaste opportuniteitsdetector implementeren
title: Een aangepaste opportuniteitsdetector implementeren
uuid: 012527c5-4ef0-4cd6-a9df-2fb861078a7e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 2%

---


# Een aangepaste opportuniteitsdetector {#implement-a-custom-opportunity-detector} implementeren

U kunt uw eigen opportuniteitsdetectors implementeren door de interface PlacementOpportunityDetector te implementeren.

1. Een aangepaste `AdvertisingFactory`-instantie maken en `createOpportunityDetector` overschrijven. Bijvoorbeeld:

   ```java
   new AdvertisingFactory() { 
       ... 
       @Override 
       public PlacementOpportunityDetector createOpportunityDetector(MediaPlayerItem item) { 
           return new CustomPlacementOpportunityDetector(); 
       } 
       ... 
   }
   ```

1. Registreer de fabriek van de advertentiecliënt aan `MediaPlayer`. Bijvoorbeeld:

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Maak een aangepaste opportuniteitsdetectorklasse die de klasse `PlacementOpportunityDetector` uitbreidt.
   1. Overschrijf deze functie in de aangepaste opportuniteitsdetector:

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      De `timedMetadataList` bevat de lijst van beschikbare `TimedMetadata`, die wordt gesorteerd. Metagegevens bevatten de doelparameters en de aangepaste parameters die naar de advertentieprovider moeten worden verzonden.

   1. Maak voor elke `TimedMetadata` een `List<PlacementOpportunity>`. De lijst mag leeg zijn, maar niet null. `PlacementOpportunity` moeten de volgende kenmerken hebben:

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. Nadat de plaatsingskansen voor alle ontdekte getimed meta-gegevensvoorwerpen worden gecreeerd, keer eenvoudig de `PlacementOpportunity` lijst terug.

Dit is een voorbeeld van een aangepaste plaatsingsopportuniteitsdetector:

```java
public class CustomPlacementOpportunityDetector implements PlacementOpportunityDetector { 
    ... 
    @Override 
    public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata) { 
        ... 
        List<PlacementOpportunity> opportunities = new ArrayList<PlacementOpportunity>(); 
 
        for (TimedMetadata timedMetadata : timedMetadataList) { 
 
            if (isOpportunity(timedMetadata)) {        // check if given timedMetadata should be  
                                                       // considered as an opportunity 
 
                // create an object of PlacementOpportunity and add it to the opportunities list 
                PlacementOpportunity opportunity =  
                  createPlacementOpportunity(timedMetadata, airingId, metadata); 
                Opportunities.add(opportunity); 
            } 
        } 
        return opportunities; 
    }    
    ... 
} 
```

