---
description: U kunt uw eigen opportuniteitsdetectors implementeren.
title: Een aangepaste opportuniteitsdetector implementeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Een aangepaste opportuniteitsdetector implementeren{#implement-a-custom-opportunity-detector}

U kunt uw eigen opportuniteitsdetectors implementeren.

* Als uw opportuniteitsgenerator is gebaseerd op `TimedMetadata` objecten die aan de huidige mediastream zijn gekoppeld, moet deze de `SpliceOutOpportunityGenerator` of `TimedMetadataOpportunityGenerator`.

* Als uw opportuniteitsgenerator is gebaseerd op out-of-band gegevens die door een externe dienst (zoals een CIS) worden verstrekt, dan moet het de `OpportunityGenerator`.

1. Maak de aangepaste opportuniteitsgenerator.

       Als uw aangepaste opportuniteitsgenerator is gebaseerd op objecten TimedMetadata, breidt u de klasse TimedMetadataOpportunityGenerator uit en overschrijft u deze methoden:
   
   * `doConfigure` - Deze methode wordt aangeroepen nadat het mediaspelitem is gemaakt en biedt de opportuniteitsgenerator de mogelijkheid om indien nodig een eerste set mogelijkheden te maken
   * `doProcess` - Deze methode wordt telkens aangeroepen wanneer een nieuwe `TimedMetadata` wordt gedetecteerd (bijvoorbeeld voor live/lineaire streams telkens wanneer de afspeellijst/manifest wordt vernieuwd)

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

1. Registreer de aangepaste inhoudsfabriek voor de af te spelen mediastream.

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
