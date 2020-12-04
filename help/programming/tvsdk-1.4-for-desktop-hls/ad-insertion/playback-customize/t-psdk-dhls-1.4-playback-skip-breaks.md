---
description: Standaard dwingt TVSDK een advertentie-einde af wanneer de gebruiker een advertentie-einde zoekt. U kunt het gedrag aanpassen om een advertentie-einde over te slaan als de tijd die is verstreken vanaf een vorige eindemarkering binnen een bepaald aantal minuten is.
seo-description: Standaard dwingt TVSDK een advertentie-einde af wanneer de gebruiker een advertentie-einde zoekt. U kunt het gedrag aanpassen om een advertentie-einde over te slaan als de tijd die is verstreken vanaf een vorige eindemarkering binnen een bepaald aantal minuten is.
seo-title: Advertenties gedurende een bepaalde periode overslaan
title: Advertenties gedurende een bepaalde periode overslaan
uuid: 1a18d5fd-c957-481b-83ae-2129590c1678
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Overslaan en afbreken voor een bepaalde tijd{#skip-ad-breaks-for-a-period-of-time}

Standaard dwingt TVSDK een advertentie-einde af wanneer de gebruiker een advertentie-einde zoekt. U kunt het gedrag aanpassen om een advertentie-einde over te slaan als de tijd die is verstreken vanaf een vorige eindemarkering binnen een bepaald aantal minuten is.

>[!IMPORTANT]
>
>Wanneer er een interne zoekactie is om een advertentie over te slaan, kan het zijn dat er een kleine pauze is in het afspelen.

In het volgende voorbeeld van een aangepaste advertentiebeleidskiezer worden advertenties in de komende vijf minuten (tijd van de wandklok) overgeslagen nadat een gebruiker een advertentiesonderbreking heeft bekeken.

1. Breid de standaardselecteur van het advertentiebeleid uit om het standaardgedrag met voeten te treden.

   ```
   /** 
    * Custom ad policy selector. 
    */ 
   public class CustomAdPolicySelector extends DefaultAdPolicySelector { 
   
       /** 
        * Default constructor. 
        * 
        * @param item Associated media player item. 
        */ 
       public function CustomAdPolicySelector(item:MediaPlayerItem) { 
           super(item); 
   
           item.player.addEventListener(AdBreakPlaybackEvent.AD_BREAK_COMPLETED,  
                                        onAdBreakCompleted); 
       } 
   
       override public function selectPolicyForAdBreak(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForAdBreak(adPolicyInfo); 
           } 
   
           return AdBreakPolicy.SKIP; 
       } 
   
       override public function selectAdBreaksToPlay(adPolicyInfo:AdPolicyInfo):Vector.<AdBreakTimelineItem> { 
           if (shouldPlayAds()) { 
               return super.selectAdBreaksToPlay(adPolicyInfo); 
           } 
   
           return new Vector.<AdBreakTimelineItem>(); 
       } 
   
       override public function selectPolicyForSeekIntoAd(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForSeekIntoAd(adPolicyInfo); 
           } 
   
           return AdPolicy.SKIP_TO_NEXT_AD_IN_AD_BREAK; 
       } 
   
       private function onAdBreakCompleted(event:AdBreakPlaybackEvent):void { 
           _lastAdBreakPlayedTime = new Date().valueOf(); 
       } 
   
       private function shouldPlayAds():Boolean { 
           var currentTime:Number = new Date().valueOf(); 
           return isNaN(_lastAdBreakPlayedTime) 
                   ||  (currentTime - _lastAdBreakPlayedTime > _minimumInterval); 
       } 
   
       private var _lastAdBreakPlayedTime:Number = NaN; 
       private var _minimumInterval:Number = 300000; // 5 minutes in milliseconds 
   }
   ```

1. Maak een nieuwe advertentiefabriek die uw aangepaste kiezer gebruikt.

   ```
   public class CustomAdPolicyContentFactory extends DefaultContentFactory { 
   
       private var _adPolicySelector:CustomAdPolicySelector; 
   
       /** 
        * Default constructor. 
        */ 
       public function CustomAdPolicyContentFactory() { 
   
       } 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
       if (!_adPolicySelector) { 
           _adPolicySelector = new CustomAdPolicySelector(item); 
       } 
   
       return _adPolicySelector; 
       } 
   }
   ```

1. Registreer de nieuwe reclamefabrieklasse die met MediaPlayer moet worden gebruikt.

   ```
   var mediaResource:MediaResource =  
     MediaResource.createFromUrl("https://example.org/stream.m3u8", null); 
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     PSDKConfig.retrieveMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomAdPolicyContentFactory(); 
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

