---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
seo-description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
seo-title: Standaardgedrag voor afspelen gebruiken
title: Standaardgedrag voor afspelen gebruiken
uuid: 20785251-eb2f-4cc0-b919-1a88c0b1c57c
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Standaardgedrag voor afspelen gebruiken {#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

1. Als u standaardgedrag wilt gebruiken, voert u een van de volgende taken uit:

   * Als u uw eigen `AdvertisingFactory` klasse uitvoert, terugkeer ongeldig voor `createAdPolicySelector`.

   * Als u geen douaneimplementatie voor de `AdvertisingFactory` klasse hebt, gebruikt TVSDK een gebrek en beleidsselecteur.

## Aangepaste weergave instellen {#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties bij TVSDK voordat u gedrag voor advertenties aanpast of overschrijft.

* Implementeer de interface `AdPolicySelector` en alle bijbehorende methoden.

   Deze optie wordt aanbevolen als u **all** de standaard en het gedrag moet negeren.

* Breid de `DefaultAdPolicySelector` klasse uit en verstrekt implementaties voor slechts die gedrag dat aanpassing vereist.

   Deze optie wordt geadviseerd als u slechts **sommige** van het standaardgedrag moet met voeten treden.

Zo past u het gedrag van advertenties aan:

1. Implementeer de interface `AdPolicySelector` en alle bijbehorende methoden.
1. Wijs het beleidsexemplaar toe dat door TVSDK via de reclamefabriek moet worden gebruikt.

   >[!NOTE]
   >
   >Aangepast advertentiebeleid dat aan het begin van het afspelen is geregistreerd, wordt gewist wanneer de `MediaPlayer`-instantie wordt gedealdeerd. Elke keer dat een nieuwe afspeelsessie wordt gemaakt, moet uw toepassing een beleidsselector registreren.

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