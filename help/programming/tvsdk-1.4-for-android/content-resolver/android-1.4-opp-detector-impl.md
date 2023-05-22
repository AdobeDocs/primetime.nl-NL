---
description: U kunt uw eigen opportuniteitsdetectors implementeren door de interface PlacementOpportunityDetector te implementeren.
title: Een aangepaste opportuniteitsdetector implementeren
exl-id: d78949a0-2c76-4976-9358-05f3db86781e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Een aangepaste opportuniteitsdetector implementeren {#implement-a-custom-opportunity-detector}

U kunt uw eigen opportuniteitsdetectors implementeren door de interface PlacementOpportunityDetector te implementeren.

1. Een aangepaste `AdvertisingFactory` instantie en overschrijving `createOpportunityDetector`. Bijvoorbeeld:

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

1. De advertentiecliënt registreren bij `MediaPlayer`. Bijvoorbeeld:

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Een aangepaste opportuniteitsdetectorklasse maken die de klasse `PlacementOpportunityDetector` klasse.
   1. Overschrijf deze functie in de aangepaste opportuniteitsdetector:

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      De `timedMetadataList` bevat de lijst met beschikbare `TimedMetadata`, die wordt gesorteerd. Metagegevens bevatten de doelparameters en de aangepaste parameters die naar de advertentieprovider moeten worden verzonden.

   1. Voor elke `TimedMetadata`, een `List<PlacementOpportunity>`. De lijst mag leeg zijn, maar niet null. `PlacementOpportunity` moeten de volgende kenmerken hebben:

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. Nadat de plaatsingsmogelijkheden voor alle ontdekte getimede meta-gegevensvoorwerpen worden gecreeerd, keer eenvoudig terug `PlacementOpportunity` lijst.

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
