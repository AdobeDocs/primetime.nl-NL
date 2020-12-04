---
description: In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.
seo-description: In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.
seo-title: PlayerFragment
title: PlayerFragment
uuid: 83f02c31-f3b1-4d16-97c8-5b391e8c999a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# PlayerFragment {#playerfragment}

In de klasse PlayerFragment kunt u de code bewerken om de functiemanagers volledig in te schakelen.

De klasse `PlayerFragment` bevat alle UI-componenten zoals `playerFrame`, `ControlBar`, `playerClickableAdFragment` en `adOverlay`.

De toepassing handelt de initialisatie van al deze componenten af, evenals het maken van de speler, het instellen van de weergaven, het maken van functiebeheer voor de mediaspeler, het afhandelen van media-gebeurtenissen zoals resume, play, en het pauzeren en afhandelen van de gebeurtenislisteners voor `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager` en `EntitlementManager`.`PlaybackManager`

Het dossier van XML dat de configuratieparameters voor `PlayerFragment` omvat is `res/layout/fragment_player.xml`.

Voordat u de functiemanagers maakt, moet u de mediaspeler maken door ervoor te zorgen dat de volgende code in het bestand `PlayerFragment.java` staat:

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
