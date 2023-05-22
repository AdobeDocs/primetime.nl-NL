---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
title: Standaardgedrag voor afspelen gebruiken
exl-id: 0ea3d2bb-b4d4-4090-ab5f-b6c31c1abe32
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Standaardgedrag voor afspelen gebruiken {#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

1. Als u standaardgedrag wilt gebruiken, voert u een van de volgende taken uit:

   * Als u uw eigen `AdvertisingFactory` klasse, null retourneren voor `createAdPolicySelector`.

   * Als u geen aangepaste implementatie voor de `AdvertisingFactory` -klasse gebruikt TVSDK een standaardkiezer voor advertentiebeleid.

## Aangepast afspelen instellen {#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties met voordat u gedrag voor advertenties kunt aanpassen of overschrijven.
Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Implementeer de `AdPolicySelector` en alle bijbehorende methoden.

   Deze optie wordt aanbevolen als u deze optie moet overschrijven **alles** de standaardinstellingen en gedragingen.

* Breid uit `DefaultAdPolicySelector` en verstrekt implementaties voor slechts die gedrag dat aanpassing vereist.

   Deze optie wordt aanbevolen als u alleen de optie wilt overschrijven **sommige** van het standaardgedrag.

Zo past u het gedrag van advertenties aan:

1. Implementeer de `AdPolicySelector` en alle methoden ervan.
1. Wijs het beleidsexemplaar toe dat door TVSDK via de reclamefabriek moet worden gebruikt.

   >[!NOTE]
   >
   >de klasse CustomContentFactory extends ContentFactory&amp;segment;
   >...
   >@Override
   >public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem)&amp;segment;
   >retourneert nieuwe CustomAdPolicySelector(mediaPlayerItem);
   >&amp;Bron;
   >...
   >&amp;Bron;
   >// registreer de aangepaste inhoudsfabriek met de mediaspeler.
   >MediaPlayerItemConfig config = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >// deze configuratie wordt later doorgegeven tijdens het laden >de resource
   >mediaPlayer.replaceCurrentResource(resource, config);

1. Implementeer uw aanpassingen.
