---
description: U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.
seo-description: U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.
seo-title: Een aangepaste contentoplosser implementeren
title: Een aangepaste contentoplosser implementeren
uuid: cf85dd90-242e-4f9e-9785-158ca0fc9465
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Een aangepaste contentoplosser implementeren{#implement-a-custom-content-resolver}

U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.

Wanneer Browser TVSDK een nieuwe kans ontdekt, herhaalt het door de geregistreerde inhoudoplossers zoekend één die die kans kan oplossen door de `canResolve` methode te gebruiken. De eerste die waar terugkeert wordt geselecteerd voor het oplossen van de kans. Als er geen inhoudoplosser kan worden gemaakt, wordt die mogelijkheid overgeslagen. Omdat het proces voor het oplossen van inhoud meestal asynchroon is, is de oplosser van de inhoud verantwoordelijk voor het op de hoogte brengen van Browser TVSDK wanneer het proces is voltooid.

De volgende informatie onthouden:

* De inhoudoplosser roept `client.process` op om op te geven welke tijdlijnbewerking TVSDK moet uitvoeren.

   De bewerking is doorgaans een plaatsing van een advertentie-einde.

* De inhoudoplosser roept aan `client.notifyCompleted` als het oplossend proces succesvol is of `client.notifyFailed` als het proces ontbreekt.

1. Maak een aangepaste opportuniteitsoplosser.

   ```js
   /** 
     * Class implementing AdobePSDK.ContentResolver interface  
   */ 
   CustomResolver = function () { 
   }; 
   
   CustomResolver.prototype = { 
       constructor: CustomResolver, 
       configureCallbackFunc: function (item, client) { 
       // here you can read any media stream characteristics which 
       // might help configure your content resolver like 
       // - the media player item configuration through the item.config 
       // - the media resource metadata through item.resource.metadata 
      }, 
   
       canResolveCallbackFunc: function (opportunity) { 
       // check if the opportunity can be resolved by this resolver 
       // if yes return true, otherwise return false 
       return true; 
      }, 
   
       resolveCallbackFunc: function (opportunity) {         
       // start the resolving process 
       // communicate with your custom ad server 
   
       // in this example we assume that: 
       // - if successful, onResolveCompleted method will be invoked 
       // - if failed, onResolveFailed method will be invoked 
      }, 
   
       onResolveCompleted: function (response) { 
        try { 
           var proposals = []; 
           // extract the timeline ad placement from the response 
           // and add them to the proposal vector 
           // - extract the ad break 
           // - calculate the placement (can reuse the _opportunity.placement) 
           // var timelineOperation = new AdobePSDK.AdBreakPlacement (adBreak, placement); 
           // proposals.push (timelineOperation); 
   
           client.process (proposals); 
           client.notifyCompleted (_opportunity); 
       } catch (error) { 
           onResolveFailed (error); 
       } 
   }, 
   
       onResolveFailed: function (error) { 
         client.notifyFailed (_opportunity); 
       } 
   
   }; 
   ```

1. Maak de aangepaste inhoudsfabriek die de aangepaste inhoudsoplosser gebruikt.

   Bijvoorbeeld:

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
       constructor: CustomContentFactory, 
       retrieveResolversCallbackFunc: function (item) { 
           var result = []; 
           var resource = item.resource; 
           if (resource.metadata.containsKey("custom-opportunity-detector")) { 
               result.push (new CustomResolver()); 
           } 
           return result; 
       }, 
       … 
   }; 
   ```

1. Registreer de aangepaste inhoudsfabriek voor de mediastream die moet worden afgespeeld.

   In de UI Framework-speler kunt u als volgt de fabriek voor aangepaste inhoud opgeven:

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var advertisingMetadata = new AdobePSDK.AdvertisingMetadata(); 
   // set any parameter you need for custom ad resolver 
   // advertisingMetadata.setValue ("customparam", "customvalue"); 
   
   var metadata = new AdobePSDK.Metadata(); 
   metadata.setMetadata ("custom-opportunity-detector", advertisingMetadata); 
   
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
       mediaPlayerItemConfig: { 
              advertisingFactory: advertisingFactory 
       }, 
          mediaResource: { 
                  resourceUrl:'Specify Resource Url', 
                  metadata: metadata 
          } 
   } 
   
   }); 
   ```

