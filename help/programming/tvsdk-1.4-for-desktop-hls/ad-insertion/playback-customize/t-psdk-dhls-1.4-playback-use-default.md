---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
title: Standaardgedrag voor afspelen gebruiken
exl-id: 8d25e076-4335-49c8-b6b8-f2694b1b9074
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
