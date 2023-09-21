---
description: De interface MediaPlayer omvat de functionaliteit en het gedrag van een media speler.
title: De MediaPlayer instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# De MediaPlayer instellen {#set-up-the-mediaplayer}

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze aan te sluiten op de weergave van de mediaspeler in TVSDK, die beschikt over methoden om video&#39;s af te spelen en te beheren. TVSDK beschikt bijvoorbeeld over afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform maken en de knoppen instellen om deze TVSDK-methoden aan te roepen. De MediaPlayer-interface omvat de functionaliteit en het gedrag van een mediaspeler.

TVSDK biedt één implementatie van de `MediaPlayer` interface: de klasse DefaultMediaPlayer. Instantieer wanneer u functionaliteit voor het afspelen van video nodig hebt `DefaultMediaPlayer`.

>[!NOTE]
>
>Interactie met de `DefaultMediaPlayer` instantie alleen met de methoden die door de `MediaPlayer` interface.

1. Instantiëren van een `MediaPlayerContext` met het laden van de toepassing `authorizedFeatures` instantie (zie [Uw ondertekende token laden](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)).

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. Instantiëren van een `MediaPlayer` met de methode public maakt u een fabrieksmap en geeft u een `MediaPlayerContext` contextobject:

   ```
   public static function create(context:Context):MediaPlayer
   ```

   Dit retourneert een algemeen `MediaPlayer` interface. 1. Instantiëren van een `MediaPlayerView` en geef de StageVideo-instantie op die moet worden gebruikt:

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. Koppel de `MediaPlayerView` -instantie met de nieuwe weergave:

   ```
   mediaPlayer.view = view;
   ```

1. Plaats de `MediaPlayerView` -instantie op het scherm van het apparaat:

   ```
   container.addChild(view)
   ```

De `MediaPlayer` -instantie is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.
