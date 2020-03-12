---
description: In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.
seo-description: In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.
seo-title: PlayerFragment
title: PlayerFragment
uuid: 83f02c31-f3b1-4d16-97c8-5b391e8c999a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# PlayerFragment {#playerfragment}

In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.

De `PlayerFragment` klasse bevat alle UI-componenten zoals de `playerFrame`, `ControlBar`, `playerClickableAdFragment`en `adOverlay`.

Het handelt de initialisatie van al deze componenten af, evenals het creëren van de speler, het opzetten van de meningen, het creëren van eigenschapmanagers voor de media speler, het behandelen van media gebeurtenissen zoals hervatten, spelen, en pauzeren en het behandelen van de gebeurtenisluisteraars voor `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager`, `PlaybackManager`en `EntitlementManager`.

Het XML-bestand dat de configuratieparameters voor het `PlayerFragment` bestand bevat, is `res/layout/fragment_player.xml`.

Voordat u de functiemanagers maakt, moet u de mediaspeler maken door ervoor te zorgen dat de volgende code in het `PlayerFragment.java` bestand staat:

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
