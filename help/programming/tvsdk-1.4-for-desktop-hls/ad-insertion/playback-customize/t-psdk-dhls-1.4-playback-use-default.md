---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
title: Standaardgedrag voor afspelen gebruiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---


# Standaardafspeelgedrag gebruiken{#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

Standaardgedrag gebruiken:

* Als u uw eigen `ContentFactory` klasse uitvoert, keer een nieuwe geval van `DefaultAdPolicySelector` in uw implementatie van `doRetrieveAdPolicySelector` terug.

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

* Als u geen aangepaste implementatie voor de klasse `ContentFactory` hebt, gebruikt TVSDK `DefaultAdPolicySelector`.