---
title: Onvolledige invoeging van advertentie-einde
description: Onvolledige invoeging van advertentie-einde
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Onvolledige invoeging van advertentie-einde {#partial-ad-break-insertion}

U kunt een tv-achtige ervaring inschakelen om in live streams deel te kunnen nemen aan een advertentie. Met de functie Partial Ad break kunt u een tv-achtige ervaring nabootsen waarbij, als de client een live stream in een midroll start, deze binnen die midroll start. Het is vergelijkbaar met het schakelen naar een tv-zender en de reclames werken naadloos.

Als een gebruiker zich bijvoorbeeld in het midden van een 90-seconde ad-onderbreking (drie 30-secondenadvertenties), 10 seconden in de tweede advertentie aanmeldt (dat wil zeggen, bij 40 seconden in de ad-onderbreking), gebeurt het volgende:

* De tweede advertentie wordt afgespeeld voor de resterende duur (20 sec.), gevolgd door de derde advertentie.
* Trackers voor de gedeeltelijk afgespeelde advertentie (de tweede advertentie) worden niet geactiveerd. Alleen de tracker voor de derde advertentie wordt geactiveerd.

Dit gedrag is niet standaard ingeschakeld. Ga als volgt te werk om deze functie in te schakelen in uw app:

1. Schakel live prerolls uit met de methode setEnableLivePreroll van de klasse AdvertisingMetadata.

   ```
   advertisingMetadata.setLivePreroll(false)  
   advertisingMetadata.setPreroll(false)
   ```

1. Schakel de voorkeur voor Gedeeltelijke invoeging van advertentie in. Gebruik de nieuwe methode setPartialAdBreakPref in de interface MediaPlayer om deze functie AAN te schakelen. Gebruik de methode getPartialAdBreakPref om de huidige status van deze voorkeur te vinden.

   ```
   MediaPlayer mediaPlayer = new MediaPlayer(getActivity().getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
   ```
