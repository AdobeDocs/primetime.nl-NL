---
description: In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.
title: PlayerFragment
exl-id: 9060f0f5-9148-48cd-b89b-718607dd70bc
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# PlayerFragment {#playerfragment}

In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.

De `PlayerFragment` klasse bevat alle UI-componenten, zoals de klasse `playerFrame`, `ControlBar`, `playerClickableAdFragment`, en `adOverlay`.

De toepassing handelt de initialisatie van al deze componenten af, en maakt de speler, stelt de weergaven in, maakt functiemanagers voor de mediaspeler, verwerkt media-gebeurtenissen zoals resume, play en pauzeren en afhandelen van de gebeurtenislisteners voor `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager`, `PlaybackManager`, en `EntitlementManager`.

Het XML-bestand met de configuratieparameters voor de `PlayerFragment` is `res/layout/fragment_player.xml`.

Voordat u de functiemanagers maakt, moet u de mediaspeler maken door ervoor te zorgen dat de volgende code in het dialoogvenster `PlayerFragment.java` bestand:

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
