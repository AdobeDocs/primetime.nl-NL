---
description: U kunt uw eigen opportuniteitsgenerator uitvoeren door de interface OpportunityGenerator uit te breiden.
seo-description: U kunt uw eigen opportuniteitsgenerator uitvoeren door de interface OpportunityGenerator uit te breiden.
seo-title: Een aangepaste opportuniteitsgenerator implementeren
title: Een aangepaste opportuniteitsgenerator implementeren
uuid: b80da2da-32d5-41f7-86ca-936d6f25b015
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Een aangepaste opportuniteitsgenerator implementeren{#implement-a-custom-opportunity-generator}

U kunt uw eigen opportuniteitsgenerator uitvoeren door de interface OpportunityGenerator uit te breiden.

1. Maak de aangepaste opportuniteitsgenerator.

   Bijvoorbeeld:

   ```js
   /** 
   * Class implementing AdobePSDK.OpportunityGenerator interface 
   */ 
   CustomOpportunityGenerator = function () { 
   }; 
   
   CustomOpportunityGenerator.prototype = { 
       constructor: CustomOpportunityGenerator, 
       configureCallbackFunc: function (item, client, mode, playhead, playbackRange) {  
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current AdobePSDK.MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadatas = item.timedMetadata; 
       }, 
       updateCallbackFunc: function (playhead, playbackRange) { 
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve (opportunity); 
       }, 
       … 
   }; 
   ```

1. Creeer de fabriek van de douaneinhoud, die de generator van de douanemogelijkheid gebruikt.

   Bijvoorbeeld:

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
          constructor: CustomContentFactory, 
          retrieveOpportunityGeneratorsCallbackFunc: function (item) { 
               var result = []; 
               result.push (new CustomOpportunityGenerator()); 
               return result; 
       }, 
       … 
   }; 
   ```

1. Registreer de aangepaste inhoudsfabriek voor de mediastream die moet worden afgespeeld.

   In UI Framework-speler kunt u als volgt de fabriek voor aangepaste inhoud opgeven:

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
           mediaPlayerItemConfig: { 
                   advertisingFactory: advertisingFactory 
           }, 
               mediaResource: { 
                   resourceUrl:'Specify Resource Url' 
          } 
     } 
   }); 
   ```

