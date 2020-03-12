---
description: U kunt het gedrag van advertenties aanpassen of overschrijven.
seo-description: U kunt het gedrag van advertenties aanpassen of overschrijven.
seo-title: Aangepast afspelen instellen
title: Aangepast afspelen instellen
uuid: 479ca1b0-6b3f-42fa-85e1-31d707da8730
translation-type: tm+mt
source-git-commit: a21a5fcc819a7bec58ad36e118d04f462ec3fd92

---


# Aangepast afspelen instellen{#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties met voordat u gedrag voor advertenties kunt aanpassen of overschrijven.
Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Voer de `AdPolicySelector` interface en al zijn methodes uit.

   Deze optie wordt aanbevolen als u **alle** standaardgedragingen wilt negeren.

* Breid de `DefaultAdPolicySelector` klasse uit en verstrek implementaties voor slechts die gedrag dat aanpassing vereist.

   Deze optie wordt aanbevolen als u slechts **enkele** standaardgedragingen wilt overschrijven.

Voer voor beide opties de volgende taken uit:

1. Implementeer uw eigen aangepaste advertentiebeleidskiezer.

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
   >Als de fabriek van de douaneinhoud voor een specifieke stroom door de `MediaPlayerItemConfig` klasse werd geregistreerd, zal het worden ontruimd wanneer de `MediaPlayer` instantie wordt toegewezen. Uw toepassing moet deze registreren telkens wanneer een nieuwe afspeelsessie wordt gemaakt.