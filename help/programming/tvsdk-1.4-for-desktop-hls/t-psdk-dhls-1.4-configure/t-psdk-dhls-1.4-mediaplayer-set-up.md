---
description: De interface MediaPlayer omvat de functionaliteit en het gedrag van een media speler.
title: De MediaPlayer instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# MediaPlayer {#set-up-the-mediaplayer} instellen

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze aan te sluiten op de weergave van de mediaspeler in TVSDK, die beschikt over methoden om video&#39;s af te spelen en te beheren. TVSDK beschikt bijvoorbeeld over afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform maken en de knoppen instellen om deze TVSDK-methoden aan te roepen. De MediaPlayer-interface omvat de functionaliteit en het gedrag van een mediaspeler.

TVSDK biedt één implementatie van de interface `MediaPlayer`: de klasse DefaultMediaPlayer. Instantieer `DefaultMediaPlayer` wanneer u functionaliteit voor het afspelen van video nodig hebt.

>[!NOTE]
>
>Interactie met de `DefaultMediaPlayer` instantie slechts met de methodes die door de `MediaPlayer` interface worden blootgesteld.

1. Instantieer een `MediaPlayerContext` gebruikend de application-loaded `authorizedFeatures` instantie (zie [Laad uw ondertekend teken](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)).

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instantiëren van een `MediaPlayer` met de methode public maakt factory-methode, waarbij een contextobject `MediaPlayerContext` wordt doorgegeven:

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Dit keert een generische `MediaPlayer` interface terug. 1. Instantieer een `MediaPlayerView` en geef de StageVideo-instantie op die moet worden gebruikt:

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Koppel de instantie `MediaPlayerView` aan de nieuwe weergave:

   ```
   mediaPlayer.view = view;
   ```

1. Plaats de `MediaPlayerView` instantie op het scherm van het apparaat:

   ```
   container.addChild(view)
   ```

De instantie `MediaPlayer` is nu beschikbaar en correct geconfigureerd om video-inhoud weer te geven op het apparaatscherm.