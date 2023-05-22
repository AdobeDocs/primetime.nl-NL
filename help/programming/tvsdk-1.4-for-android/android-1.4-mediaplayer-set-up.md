---
description: De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.
title: De MediaPlayer instellen
exl-id: 2698fe8d-0b73-4aad-9fee-55d034d8ca64
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# De MediaPlayer instellen {#set-up-the-mediaplayer}

De MediaPlayer-interface voor Android omvat de functionaliteit en het gedrag van een mediaspeler.

TVSDK biedt één implementatie van de `MediaPlayer` interface, de `DefaultMediaPlayer` klasse. Instantieer wanneer u functionaliteit voor het afspelen van video nodig hebt `DefaultMediaPlayer`.

>[!TIP]
>
>Interactie met de `DefaultMediaPlayer` instantie alleen met de methoden die door de `MediaPlayer` interface.

1. Een MediaPlayer instantiëren met behulp van het publiek `DefaultMediaPlayer.create` -fabrieksmethode, waarbij een Java Android-toepassingscontextobject wordt doorgegeven.

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. Bellen `MediaPlayer.getView` om een verwijzing naar de `MediaPlayerView` -instantie.

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. Plaats de `MediaPlayerView` instantie in een `FrameLayout` -instantie, die de video op het scherm van het apparaat plaatst.

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

De `MediaPlayer` -instantie is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.
