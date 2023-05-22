---
description: U kunt het gedrag van advertenties aanpassen of overschrijven.
title: Aangepast afspelen instellen
exl-id: 28c28589-9e94-40de-b921-1bffc0392c29
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Aangepast afspelen instellen{#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties met voordat u gedrag voor advertenties kunt aanpassen of overschrijven.
Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Implementeer de `AdPolicySelector` en alle bijbehorende methoden.

   Deze optie wordt aanbevolen als u deze optie moet overschrijven **alles** de standaardinstellingen en gedragingen.

* Breid uit `DefaultAdPolicySelector` en verstrekt implementaties voor slechts die gedrag dat aanpassing vereist.

   Deze optie wordt aanbevolen als u alleen de optie wilt overschrijven **sommige** van het standaardgedrag.

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
   >Als de fabriek met aangepaste inhoud voor een specifieke stream is geregistreerd via het dialoogvenster `MediaPlayerItemConfig` -klasse, wordt deze gewist wanneer de `MediaPlayer` -instantie wordt gedeallocatie. Uw toepassing moet deze registreren telkens wanneer een nieuwe afspeelsessie wordt gemaakt.
