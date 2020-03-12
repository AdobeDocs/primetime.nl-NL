---
description: De interface MediaPlayer omvat de functionaliteit en het gedrag van een media speler.
seo-description: De interface MediaPlayer omvat de functionaliteit en het gedrag van een media speler.
seo-title: De MediaPlayer instellen
title: De MediaPlayer instellen
uuid: 4b27643c-9ccd-4abb-9793-475d06ee2a88
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# De MediaPlayer instellen {#set-up-the-mediaplayer}

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze aan te sluiten op de weergave van de mediaspeler in TVSDK, die beschikt over methoden om video&#39;s af te spelen en te beheren. TVSDK beschikt bijvoorbeeld over afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform maken en de knoppen instellen om deze TVSDK-methoden aan te roepen. De MediaPlayer-interface omvat de functionaliteit en het gedrag van een mediaspeler.

TVSDK biedt één implementatie van de `MediaPlayer` interface: de klasse DefaultMediaPlayer. Instantieer de functie voor het afspelen van video&#39;s wanneer u deze nodig hebt `DefaultMediaPlayer`.

>[!NOTE]
>
>Interactie met de `DefaultMediaPlayer` instantie slechts met de methodes die door de `MediaPlayer` interface worden blootgesteld.

1. Instantieer een `MediaPlayerContext` instantie die door de toepassing is geladen (zie `authorizedFeatures` Uw ondertekende token [](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)laden).

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instantieer een `MediaPlayer` gebruiker die de openbare methode gebruikt creeert fabrieksmethode, die een `MediaPlayerContext` contextvoorwerp overgaat:

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Dit keert een generische `MediaPlayer` interface terug. 1. Instantieer een instantie `MediaPlayerView` en geef op welke StageVideo-instantie moet worden gebruikt:

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Koppel de `MediaPlayerView` instantie aan de nieuwe weergave:

   ```
   mediaPlayer.view = view;
   ```

1. Plaats de `MediaPlayerView` instantie op het scherm van het apparaat:

   ```
   container.addChild(view)
   ```

De `MediaPlayer` instantie is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.