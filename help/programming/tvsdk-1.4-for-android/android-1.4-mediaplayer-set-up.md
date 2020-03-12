---
description: De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.
seo-description: De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.
seo-title: De MediaPlayer instellen
title: De MediaPlayer instellen
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# De MediaPlayer instellen {#set-up-the-mediaplayer}

De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.

TVSDK biedt één implementatie van de `MediaPlayer` interface, de `DefaultMediaPlayer` klasse. Instantieer het afspelen van video wanneer u functionaliteit voor afspelen van video nodig hebt `DefaultMediaPlayer`.

>[!TIP]
>
>Interactie met de `DefaultMediaPlayer` instantie slechts met de methodes die door de `MediaPlayer` interface worden blootgesteld.

1. Instantieer een MediaPlayer met behulp van de openbare `DefaultMediaPlayer.create` fabrieksmethode en geef een Java Android-toepassingscontextobject door.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Vraag `MediaPlayer.getView` om een verwijzing naar de `MediaPlayerView` instantie te krijgen.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Plaats de `MediaPlayerView` instantie in een `FrameLayout` instantie die de video op het scherm van het apparaat plaatst.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

De `MediaPlayer` instantie is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.
