---
description: U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.
title: Een aangepaste contentoplosser implementeren
exl-id: abe967a5-ced3-4e23-8671-065e256974d3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Een aangepaste contentoplosser implementeren{#implement-a-custom-content-resolver}

U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.

Wanneer TVSDK een nieuwe kans detecteert, doorloopt het de geregistreerde contentoplossers die naar een mogelijkheid zoeken die deze kans kan oplossen met behulp van de `canResolve` methode. De eerste die waar terugkeert wordt geselecteerd voor het oplossen van de kans. Als er geen inhoudoplosser kan worden gemaakt, wordt die mogelijkheid overgeslagen. Omdat het proces voor het oplossen van inhoud meestal asynchroon is, brengt de contentoplosser TVSDK op de hoogte wanneer het proces is voltooid.

* Aanroepen van de inhoudoplosser `client.place` om aan te geven welke tijdlijnbewerking TVSDK moet uitvoeren (meestal een plaatsing van een advertentie-einde).
* Aanroepen van de inhoudoplosser `client.notifyCompleted` als het afwikkelingsproces succesvol is, of `client.notifyFailed` als het proces mislukt.

1. Maak een aangepaste opportuniteitsoplosser.

   ```
   public class CustomResolver extends ContentResolver { 
   
       /** 
        * Default constructor. 
        */ 
       public function CustomResolver() { 
       } 
   
       override protected function doConfigure(item:MediaPlayerItem):void { 
           // here you can read any media stream characteristics which 
           // might help configure your content resolver like 
           // - the media player item configuration through the item.config 
           // - the media resource metadata through item.resource.metadata 
       } 
   
       /** 
        * @inheritDoc 
        */ 
       override protected function doCanResolve(opportunity:Opportunity):Boolean { 
           // check if the opportunity can be resolved by this resolver 
           // if yes return true, otherwise return false 
   
           return true; 
       } 
   
       /** 
        * @inheritDoc 
        */ 
       override protected function doResolve(opportunity:Opportunity):void { 
           // start the resolving process 
           // communicate with your custom ad server 
   
           // in this example we assume that: 
           // - if successful, onResolveCompleted method will be invoked 
           // - if failed, onResolveFailed method will be invoked 
       } 
   
       private function onResolveCompleted(response:*):void { 
           try { 
               var proposals:Vector.<TimelineOperation> = new Vector.<TimelineOperation>(); 
   
               // extract the timeline ad placement from the response 
               // and add them to the proposal vector 
               // - extract the ad break 
               // - calculate the placement ( can reuse the opportunity.placement ) 
               // var timelineOperation:AdBreakPlacement = new AdBreakPlacement(placement, adBreak); 
               // proposals.push(timelineOperation); 
   
               client.process(proposals); 
               client.notifyCompleted(_opportunity); 
           } catch (error:Error) { 
               onResolveFailed(error); 
           } 
       } 
   
       private function onResolveFailed(error:Error):void { 
   
           var errorMetadata:Metadata = new Metadata(); 
           MetadataUtils.serializeError(error, errorMetadata); 
   
           var mediaError:MediaError = new MediaError(NotificationCode.CONTENT_RESOLVING_ERROR, errorMetadata); 
           client.notifyFailed(_opportunity, mediaError); 
       } 
   
       ... 
   }
   ```

1. Maak de aangepaste inhoudsfabriek die de aangepaste inhoudsoplosser gebruikt.

   Bijvoorbeeld:

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
           ... 
   
           /** 
            * @inheritDoc 
            */ 
           override protected function  
             doRetrieveResolvers(item:MediaPlayerItem):Vector.<ContentResolver> { 
               var result:Vector.<ContentResolver> = new Vector.<ContentResolver>(); 
   
               var resource:MediaResource = item.resource; 
   
               if (resource.metadata != null) { 
                   if (resource.metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY)) { 
                       result.push(new AuditudeAdResolver()); 
                   } else if (resource.metadata.containsKey("custom-opportunity-detector")) { 
                       result.push(new CustomResolver()); 
                   } 
               } 
               return result; 
           } 
   }
   ```

1. Registreer de aangepaste inhoudsfabriek voor de mediastream die moet worden afgespeeld.

   Bijvoorbeeld:

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   var advertisingMetadata:AdvertisingMetadata = new AdvertisingMetadata(); 
   // set any parameter you need for custom ad resolver 
   // advertisingMetadata.setValue("customparam", "customvalue"); 
   
   var metadata:Metadata = new Metadata(); 
   metadata.setMetadata("custom-opportunity-detector", advertisingMetadata); 
   var mediaResource:MediaResource = MediaResource.createFromUrl(url, metadata);
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
