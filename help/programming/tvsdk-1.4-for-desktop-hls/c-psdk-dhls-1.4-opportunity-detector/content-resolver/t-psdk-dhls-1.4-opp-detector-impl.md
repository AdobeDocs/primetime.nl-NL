---
description: U kunt uw eigen opportuniteitsdetectors implementeren.
title: Een aangepaste opportuniteitsdetector implementeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# Een aangepaste opportuniteitsdetector implementeren{#implement-a-custom-opportunity-detector}

U kunt uw eigen opportuniteitsdetectors implementeren.

* Als uw opportuniteitsgenerator is gebaseerd op `TimedMetadata`-objecten die zijn gekoppeld aan de huidige mediastream, moet de `SpliceOutOpportunityGenerator` of `TimedMetadataOpportunityGenerator` worden uitgebreid.

* Als uw opportuniteitsgenerator is gebaseerd op out-of-band gegevens die worden verstrekt door een externe service (zoals een CIS), moet de `OpportunityGenerator` worden uitgebreid.

1. Maak de aangepaste opportuniteitsgenerator.

       Als uw aangepaste opportuniteitsgenerator is gebaseerd op objecten TimedMetadata, breidt u de klasse TimedMetadataOpportunityGenerator uit en overschrijft u deze methoden:
   
   * `doConfigure` - Deze methode wordt aangeroepen nadat het mediaspelitem is gemaakt en biedt de opportuniteitsgenerator de mogelijkheid om indien nodig een eerste set mogelijkheden te maken
   * `doProcess` - Deze methode wordt aangeroepen wanneer nieuwe streams  `TimedMetadata` worden gedetecteerd (bijvoorbeeld voor live/lineaire streams telkens wanneer de afspeellijst/manifest wordt vernieuwd)

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

