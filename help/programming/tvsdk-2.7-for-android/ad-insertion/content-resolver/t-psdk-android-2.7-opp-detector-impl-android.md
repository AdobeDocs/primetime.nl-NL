---
description: U kunt uw eigen opportuniteitsgenerators uitvoeren door de klasse OpportunityGenerator te implementeren.
title: Een aangepaste opportuniteitsgenerator implementeren
exl-id: 8fa97515-692c-4e34-9afb-17a5409228db
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Een aangepaste opportuniteitsgenerator implementeren {#implement-a-custom-opportunity-generator}

U kunt uw eigen opportuniteitsgenerators uitvoeren door de klasse OpportunityGenerator te implementeren.

1. Uw aangepaste versie implementeren `ContentFactory` door `ContentFactory` interface en overschrijven `retrieveGenerators`.

   Bijvoorbeeld:

   ```java
   class MyContentFactory extends ContentFactory { 
       @Override 
       public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
           List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
           generators.add(MyOpportunityGenerator(item)); 
           return generators; 
       } 
       ... 
   }
   ```

1. Registreer de `ContentFactory` aan de `MediaPlayer`.

   Bijvoorbeeld:

   ```java
   // register the custom content factory with media player 
   MediaPlayerItemConfig config =  new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new MyContentFactory()); 
   
   // this config will should be later passed while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config); 
   
   // OR use MediaPlayerItemLoader to pre-load a resource 
   id = 23; 
   itemLoader.load(resource, id, config);
   ```

1. Creeer een klasse van de douanemogelijkheid generator die uitvoert `OpportunityGenerator` klasse.

   ```java
   public class CustomOpportunityGenerator implements OpportunityGenerator  
   {...}
   ```

   1. In de generator van de douanemogelijkheid, treedt `doConfigure`, `doUpdate` en `doCleanup`:

      ```java
      @Override 
       public void configure(MediaPlayerItem item, Context context,  
       OpportunityGeneratorClient client, AdSignalingMode mode, long playhead, TimeRange playbackRange) { 
      } 
      
      protected void update(long playhead, TimeRange playbackRange){ 
      } 
      
      protected void cleanup(){ 
      }
      ```

      U kunt als volgt de metagegevens met tijdslimiet verkrijgen:

      ```java
      List<TimedMetadata> tList = getItem().getTimedMetadata(); 
      ```

   1. Voor elke `TimedMetadata` of groep `TimedMetadata`, maak een kans met de volgende kenmerken:

      ```java
      Opportunity( 
        String id,                      // Can be id from timedMetadata  
        Placement placementInformation, // Placement object containing Type, time, duration 
        Metadata metadataSettings,      // Ad metadata with targeting params sent to the ad provider 
        Metadata customParams           // Metadata for customizing resolving and/or tracking process. 
      ); 
      ```

   1. Voor elke gemaakte kans roept u `resolve` op de `OpportunityGeneratorClient:getClient().resolve(opportunity);`.

<!--<a id="example_7A46377EBE79458E87423EB95D0568D4"></a>-->

Dit is een voorbeeld van een aangepaste plaatsingsopportuniteitsdetector:

```java
public class MyOpportunityGenerator implements OpportunityGenerator {

     @Override 
      public void configure(MediaPlayerItem item, Context context,  
      OpportunityGeneratorClient client, AdSignalingMode mode, long playhead, TimeRange playbackRange) { 
      } 
 
        MediaPlayerItem item = getItem(); 
        MediaPlayerItemConfig itemConfig = item.getConfig(); 
 
        if (itemConfig == null || itemConfig.getAdvertisingMetadata() == null) { 
            // no ad metadata, no ads 
            return; 
        } 
 
        AdvertisingMetadata metadata = item.getConfig().getAdvertisingMetadata();

        AdSignalingMode mode = itemConfig.getAdSignalingMode(); 
 
        if (mode == AdSignalingMode.CUSTOM_RANGES) 
        { 
            // don't override custom ad ranges 
            return; 
        } 
 
        Placement.Type pType = (mode == AdSignalingMode.MANIFEST_CUES) ?  
                  Placement.Type.PRE_ROLL : Placement.Type.SERVER_MAP; 
        Placement.Mode pMode = Placement.Mode.DEFAULT; 
        Placement placement = new Placement(pType, playhead,  
                  Placement.UNKNOWN_DURATION, pMode); 
 
        Opportunity opportunity = new Opportunity("initialOpportunity", placement,  
                  metadata, null); 
 
        OpportunityGeneratorClient client = getClient(); 
        client.resolve(opportunity); 
    } 
 
    @Override 
    protected void update(long playhead, TimeRange playbackRange) { 
 
 ... 
 timedMetadataList = getItem().getTimedMetadata(); 
        for (TimedMetadata timedMetadata : timedMetadataList) { 
         if (isOpportunity(timedMetadata)) {   // check if given timedMetadata should  
                                               // be considered as an opportunity 
  // create a PlacementOpportunity object and add it to the opportunities list 
                Opportunity opportunity = new Opportunity("id", placement, metadata, null); 
                client.resolve(opportunity) 
          } 
        } 
    } 
 
    @Override 
    protected void cleanup() {} 
}
```
