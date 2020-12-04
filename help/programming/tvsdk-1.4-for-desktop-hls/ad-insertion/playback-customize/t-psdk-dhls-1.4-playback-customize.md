---
description: U kunt het gedrag van advertenties aanpassen of overschrijven.
seo-description: U kunt het gedrag van advertenties aanpassen of overschrijven.
seo-title: Aangepast afspelen instellen
title: Aangepast afspelen instellen
uuid: 479ca1b0-6b3f-42fa-85e1-31d707da8730
translation-type: tm+mt
source-git-commit: a21a5fcc819a7bec58ad36e118d04f462ec3fd92
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# Aangepaste weergave instellen{#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties met voordat u gedrag voor advertenties kunt aanpassen of overschrijven.
Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Implementeer de interface `AdPolicySelector` en alle bijbehorende methoden.

   Deze optie wordt aanbevolen als u **all** de standaard en het gedrag moet negeren.

* Breid de `DefaultAdPolicySelector` klasse uit en verstrekt implementaties voor slechts die gedrag dat aanpassing vereist.

   Deze optie wordt geadviseerd als u slechts **sommige** van het standaardgedrag moet met voeten treden.

Voer voor beide opties de volgende taken uit:

1. Implementeer uw eigen aangepaste advertentie-beleidskiezer.

   ```
   public class CustomAdPolicySelector implements AdPolicySelector { 
       // your own customization here 
   }
   ```

1. Breid de inhoudsfabriek uit om de selecteur van de douane en van het beleid te gebruiken.

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       /** 
        * @inheritDoc 
        */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
           return new CustomAdPolicySelector(item); 
       } 
   }
   ```

   ```
   psdkutils::PSDKSharedPointer<psdk::ContentFactory> factory; 
   psdkFactory->createDefaultContentFactory(&factory); 
   psdkutils::PSDKSharedPointer<psdk::AdPolicySelector> defaultAdPolicySelector; 
   factory->retrieveAdPolicySelector(item, &defaultAdPolicySelector);
   ```

1. Registreer de nieuwe inhoudsfabriek die door TVSDK moet worden gebruikt in de publicatieworkflow.

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >Als de fabriek van de douaneinhoud voor een specifieke stroom door de `MediaPlayerItemConfig` klasse werd geregistreerd, zal het worden ontruimd wanneer de `MediaPlayer` instantie wordt deassigned. Uw toepassing moet deze registreren telkens wanneer een nieuwe afspeelsessie wordt gemaakt.