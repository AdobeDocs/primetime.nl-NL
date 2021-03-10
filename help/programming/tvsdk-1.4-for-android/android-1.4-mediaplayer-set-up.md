---
description: De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.
title: De MediaPlayer instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# MediaPlayer {#set-up-the-mediaplayer} instellen

De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.

TVSDK biedt één implementatie van de `MediaPlayer`-interface, de `DefaultMediaPlayer`-klasse. Instantieer `DefaultMediaPlayer` wanneer u functionaliteit voor het afspelen van video nodig hebt.

>[!TIP]
>
>Interactie met de `DefaultMediaPlayer` instantie slechts met de methodes die door de `MediaPlayer` interface worden blootgesteld.

1. Instantieer een MediaPlayer met de fabrieksmethode public `DefaultMediaPlayer.create` en geef een Java Android-toepassingscontextobject door.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Roep `MediaPlayer.getView` aan om een verwijzing naar de instantie `MediaPlayerView` te krijgen.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Plaats de `MediaPlayerView` instantie in een `FrameLayout` instantie, die de video op het scherm van het apparaat plaatst.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

De instantie `MediaPlayer` is nu beschikbaar en correct geconfigureerd om video-inhoud weer te geven op het apparaatscherm.
