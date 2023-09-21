---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
title: Standaardgedrag voor afspelen gebruiken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# Standaardgedrag voor afspelen gebruiken{#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

Standaardgedrag gebruiken:

* Als u uw eigen `ContentFactory` klasse, een nieuwe instantie van `DefaultAdPolicySelector` in uw implementatie van `doRetrieveAdPolicySelector`.

  ```
  public class CustomContentFactory extends ContentFactory { 
  
      //... 
      // your custom code for advertising classes 
      //... 
  
      /** 
       * @inheritDoc 
       */ 
      override protected function  
        doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
          return new DefaultAdPolicySelector(item); 
      } 
  }
  ```

* Als u geen aangepaste implementatie voor de `ContentFactory` klasse, gebruik TVSDK `DefaultAdPolicySelector`.
