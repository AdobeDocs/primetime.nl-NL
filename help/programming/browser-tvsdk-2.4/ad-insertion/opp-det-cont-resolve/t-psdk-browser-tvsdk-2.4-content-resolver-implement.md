---
description: U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.
title: Een aangepaste contentoplosser implementeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Een aangepaste contentoplosser implementeren{#implement-a-custom-content-resolver}

U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.

Wanneer Browser TVSDK een nieuwe kans ontdekt, herhaalt het door de geregistreerde inhoudoplossers zoekend één die die kans kan oplossen door te gebruiken `canResolve` methode. De eerste die waar terugkeert wordt geselecteerd voor het oplossen van de kans. Als er geen inhoudoplosser kan worden gemaakt, wordt die mogelijkheid overgeslagen. Omdat het proces voor het oplossen van inhoud meestal asynchroon is, is de oplosser van de inhoud verantwoordelijk voor het op de hoogte brengen van Browser TVSDK wanneer het proces is voltooid.

De volgende informatie onthouden:

* Aanroepen van de inhoudoplosser `client.process` om aan te geven welke tijdlijnbewerking TVSDK moet uitvoeren.

  De bewerking is doorgaans een plaatsing van een advertentie-einde.

* Aanroepen van de inhoudoplosser `client.notifyCompleted` als het afwikkelingsproces succesvol is, of `client.notifyFailed` als het proces mislukt.

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

1. Registreer de aangepaste inhoudsfabriek voor de af te spelen mediastream.

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
