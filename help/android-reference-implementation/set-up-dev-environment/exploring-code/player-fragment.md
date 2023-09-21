---
description: In de klasse PlayerFragment kunt u de code bewerken om de functies voor volledig ingeschakelde functies te maken.
title: PlayerFragment
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# PlayerFragment {#playerfragment}

In de klasse PlayerFragment kunt u de code bewerken om de functies voor volledig ingeschakelde functies te maken.

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
