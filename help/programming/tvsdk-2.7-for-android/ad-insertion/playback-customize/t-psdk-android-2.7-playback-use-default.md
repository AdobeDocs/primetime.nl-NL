---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
title: Standaardgedrag voor afspelen gebruiken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Standaardgedrag voor afspelen gebruiken  {#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

1. Als u standaardgedrag wilt gebruiken, voert u een van de volgende taken uit:

   * Als u uw eigen `AdvertisingFactory` klasse, null retourneren voor `createAdPolicySelector`.

   * Als u geen aangepaste implementatie voor de `AdvertisingFactory` -klasse gebruikt TVSDK een standaardkiezer voor advertentiebeleid.

## Aangepast afspelen instellen {#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties bij TVSDK voordat u gedrag voor advertenties aanpast of overschrijft.

* Implementeer de `AdPolicySelector` en alle bijbehorende methoden.

  Deze optie wordt aanbevolen als u deze optie moet overschrijven **alles** de standaardinstellingen en gedragingen.

* Breid uit `DefaultAdPolicySelector` en verstrekt implementaties voor slechts die gedrag dat aanpassing vereist.

  Deze optie wordt aanbevolen als u alleen de optie wilt overschrijven **sommige** van het standaardgedrag.

Zo past u het gedrag van advertenties aan:

1. Implementeer de `AdPolicySelector` en alle methoden ervan.
1. Wijs het beleidsexemplaar toe dat door TVSDK via de reclamefabriek moet worden gebruikt.

   >[!NOTE]
   >
   >Aangepaste advertentiebeleidsregels die bij het begin van het afspelen zijn geregistreerd, worden gewist wanneer de knop `MediaPlayer` -instantie wordt gedeallocatie. Elke keer dat een nieuwe afspeelsessie wordt gemaakt, moet uw toepassing een beleidsselector registreren.

   Bijvoorbeeld:

   ```java
   class CustomContentFactory extends ContentFactory { 
       ... 
       @Override 
       public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
           return new CustomAdPolicySelector(mediaPlayerItem); 
       } 
       ... 
   } 
   
   // register the custom content factory with media player 
   MediaPlayerItemConfig config =  new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new CustomContentFactory()); 
   
   // this config will should be later passed while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config);
   ```

1. Implementeer uw aanpassingen.
