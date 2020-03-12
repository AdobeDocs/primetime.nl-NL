---
description: U kunt uw eigen opportuniteitsdetectors implementeren.
seo-description: U kunt uw eigen opportuniteitsdetectors implementeren.
seo-title: Een aangepaste opportuniteitsdetector implementeren
title: Een aangepaste opportuniteitsdetector implementeren
uuid: 18fb431b-4585-4293-92a7-b77ab7f9b7db
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Een aangepaste opportuniteitsdetector implementeren{#implement-a-custom-opportunity-detector}

U kunt uw eigen opportuniteitsdetectors implementeren.

* Als uw opportuniteitsgenerator is gebaseerd op `TimedMetadata` objecten die aan de huidige mediastream zijn gekoppeld, moet deze de extensie `SpliceOutOpportunityGenerator` of `TimedMetadataOpportunityGenerator`.

* Als uw opportuniteitsgenerator is gebaseerd op out-of-band gegevens die door een externe dienst (zoals een CIS) worden verstrekt, dan zou het de `OpportunityGenerator`moeten uitbreiden.

1. Maak de aangepaste opportuniteitsgenerator.

       Als uw aangepaste opportuniteitsgenerator is gebaseerd op objecten TimedMetadata, breidt u de klasse TimedMetadataOpportunityGenerator uit en overschrijft u deze methoden:
   
   * `doConfigure` - Deze methode wordt aangeroepen nadat het mediaspelitem is gemaakt en biedt de opportuniteitsgenerator de mogelijkheid om indien nodig een eerste set mogelijkheden te maken
   * `doProcess` - Deze methode wordt aangeroepen telkens wanneer nieuwe streams `TimedMetadata` worden gedetecteerd (bijvoorbeeld voor live/lineaire streams telkens wanneer de afspeellijst/manifest wordt vernieuwd)

   ```
   public class CustomOpportunityGenerator extends TimedMetadataOpportunityGenerator { 
       override protected function doConfigure(playhead:Number, playbackRange:TimeRange):void { 
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadataCollection:Vector.<TimedMetadata> = item.timedMetadata; 
       } 
   
       override protected function doProcess(timedMetadata:TimedMetadata):void { 
           ... 
   
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve(opportunity); 
       }  
       ... 
   }
   ```

1. Creeer de fabriek van de douaneinhoud, die de generator van de douanemogelijkheid gebruikt.

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       ... 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
           var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
           result.push(new CustomOpportunityGenerator()); 
   
           return result; 
       } 
   }
   ```

1. Registreer de aangepaste inhoudsfabriek voor de mediastream die moet worden afgespeeld.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

