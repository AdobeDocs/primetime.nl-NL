---
description: U kunt het gedrag van advertenties aanpassen of overschrijven.
title: Aangepast afspelen instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Aangepast afspelen instellen {#cset-up-customized-playback}

U kunt het gedrag van een advertentie aanpassen of overschrijven door de beleidsinstantie voor advertentie te registreren bij TVSDK.

Voer een van de volgende handelingen uit om het gedrag van advertenties aan te passen:

* Implementeer de `AdPolicySelector` en alle bijbehorende methoden.
Deze optie wordt aanbevolen als u alle standaardinstellingen en gedragingen moet negeren.

* Breid uit `DefaultAdPolicySelector` en verstrekt implementaties voor slechts die gedrag dat aanpassing vereist.
Deze optie wordt aanbevolen als u slechts enkele standaardgedragingen wilt overschrijven.

Voer voor beide opties de volgende taken uit:

Zo past u het gedrag van advertenties aan:

1. Voer de interface AdPolicySelector en al zijn methodes uit.

1. Wijs het beleidsexemplaar toe dat door TVSDK via de reclamefabriek moet worden gebruikt.

>[!IMPORTANT]
>
>Aangepaste advertentiebeleidsregels die zijn geregistreerd aan het begin van >playback worden gewist wanneer de instantie MediaPlayer >deassigned is. Uw toepassing moet een beleid >selector registreren telkens wanneer een nieuwe playbackzitting wordt gecreeerd.

Bijvoorbeeld:

```
    class CustomContentFactory extends ContentFactory {
     ...
    @Override
    public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) {
    return new CustomAdPolicySelector(mediaPlayerItem);
    }
     ...
    }
    TVSDK 1.4 for Android Programmer's Guide 46
    // register the custom content factory with media player
    MediaPlayerItemConfig config = new MediaPlayerItemConfig();
    config.setAdvertisingFactory(new CustomContentFactory());
    // this config will should be later passed while loading the resource
    mediaPlayer.replaceCurrentResource(resource, config);
```

1. Implementeer uw aanpassingen.
