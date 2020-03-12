---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
seo-description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
seo-title: Standaardgedrag voor afspelen gebruiken
title: Standaardgedrag voor afspelen gebruiken
uuid: 36f76c42-4c6c-4620-9b47-ec97519a642a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Standaardgedrag voor afspelen gebruiken {#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

1. Als u standaardgedrag wilt gebruiken, voert u een van de volgende taken uit:

   * Als u uw eigen `AdvertisingFactory` klasse implementeert, retourneert u null voor `createAdPolicySelector`.

   * Als u geen aangepaste implementatie voor de `AdvertisingFactory` klasse hebt, gebruikt TVSDK een standaard- en beleidskiezer.

## Aangepast afspelen instellen {#set-up-customized-playback}

U kunt het gedrag van advertenties aanpassen of overschrijven.

Registreer de beleidsinstantie voor advertenties met voordat u gedrag voor advertenties kunt aanpassen of overschrijven.
Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Voer de `AdPolicySelector` interface en al zijn methodes uit.

   Deze optie wordt aanbevolen als u **alle** standaardgedragingen wilt negeren.

* Breid de `DefaultAdPolicySelector` klasse uit en verstrek implementaties voor slechts die gedrag dat aanpassing vereist.

   Deze optie wordt aanbevolen als u slechts **enkele** standaardgedragingen wilt overschrijven.

Zo past u het gedrag van advertenties aan:

1. Voer de `AdPolicySelector` interface en al zijn methodes uit.
1. Wijs het beleidsexemplaar toe dat door TVSDK via de reclamefabriek moet worden gebruikt.

>[!NOTE]
>class CustomContentFactory extends ContentFactory {
>...
>@Override
>public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem) {
>retourneert nieuwe CustomAdPolicySelector(mediaPlayerItem);
>}
>...
>}
>// registreer de aangepaste inhoudsfabriek met de mediaspeler.
>MediaPlayerItemConfig config = new MediaPlayerItemConfig();
>config.setAdvertisingFactory(new CustomContentFactory());
>// deze configuratie wordt later doorgegeven tijdens het laden >de resource
>mediaPlayer.replaceCurrentResource(resource, config);

1. Implementeer uw aanpassingen.