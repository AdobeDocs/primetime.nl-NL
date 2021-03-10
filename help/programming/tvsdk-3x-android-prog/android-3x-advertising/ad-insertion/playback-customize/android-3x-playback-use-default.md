---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
title: Standaardgedrag voor afspelen gebruiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Standaardgedrag voor afspelen gebruiken {#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

1. Als u standaardgedrag wilt gebruiken, voert u een van de volgende taken uit:

   * Als u uw eigen `AdvertisingFactory` klasse uitvoert, terugkeer ongeldig voor `createAdPolicySelector`.

   * Als u geen douaneimplementatie voor de `AdvertisingFactory` klasse hebt, gebruikt TVSDK een gebrek en beleidsselecteur.

## Aangepaste weergave instellen {#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties met voordat u gedrag voor advertenties kunt aanpassen of overschrijven.
Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Implementeer de interface `AdPolicySelector` en alle bijbehorende methoden.

   Deze optie wordt aanbevolen als u **all** de standaard en het gedrag moet negeren.

* Breid de `DefaultAdPolicySelector` klasse uit en verstrekt implementaties voor slechts die gedrag dat aanpassing vereist.

   Deze optie wordt geadviseerd als u slechts **sommige** van het standaardgedrag moet met voeten treden.

Zo past u het gedrag van advertenties aan:

1. Implementeer de interface `AdPolicySelector` en alle bijbehorende methoden.
1. Wijs het beleidsexemplaar toe dat door TVSDK via de reclamefabriek moet worden gebruikt.

   >[!NOTE]
   >
   >klasse CustomContentFactory extends ContentFactory&amp;trace;
   >...
   >@Override
   >public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem) &amp;trace;
   >retourneert nieuwe CustomAdPolicySelector(mediaPlayerItem);
   >&amp;trace;
   >...
   >&amp;trace;
   >// registreer de aangepaste inhoudsfabriek met de mediaspeler.
   >MediaPlayerItemConfig config = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >// deze configuratie wordt later doorgegeven tijdens het laden >de resource
   >mediaPlayer.replaceCurrentResource(resource, config);

1. Implementeer uw aanpassingen.
