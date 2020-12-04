---
description: De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.
seo-description: De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.
seo-title: De MediaPlayer instellen
title: De MediaPlayer instellen
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '137'
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
