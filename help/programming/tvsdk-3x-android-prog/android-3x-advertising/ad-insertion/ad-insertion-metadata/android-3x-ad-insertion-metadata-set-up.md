---
description: Met de hulpklasse AuditudeSettings, die de klasse MetadataNode uitbreidt, kunt u Adobe Primetime- en beslissingsmetagegevens instellen.
seo-description: Met de hulpklasse AuditudeSettings, die de klasse MetadataNode uitbreidt, kunt u Adobe Primetime- en beslissingsmetagegevens instellen.
seo-title: Metagegevens instellen en invoegen
title: Metagegevens instellen en invoegen
uuid: 7400813c-6af0-4c96-a6c7-d9ea1ba6a7b9
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Metagegevens instellen en invoegen {#set-up-ad-insertion-metadata}

Gebruik de hulpklasse `AuditudeSettings`, die de `MetadataNode` klasse uitbreidt, om Adobe Primetime en beslissingsmetagegevens in te stellen.

>[!TIP]
>
>Adobe Primetime en het besluit was eerder bekend als Auditude.

Metagegevens voor reclame bevinden zich in de `MediaResource.Metadata` eigenschap. Wanneer u begint met het afspelen van een nieuwe video, is uw toepassing verantwoordelijk voor het instellen van de juiste metagegevens voor advertenties.

1. Maak de `AuditudeSettings` instantie.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Stel de Adobe Primetime- en beslissingsparameters `mediaID`, `zoneID`en `<ph conkeyref="phrases/primetime-sdk-name"/>`de optionele doelparameters in.

   ```java
   auditudeSettings.setZoneId("yourZoneId"); 
   auditudeSettings.setMediaId("yourVideoId"); 
   auditudeSettings.setDefaultMediaId("defVideoId"); 
   auditudeSettings.setDomain("yourAuditudeDomain"); 
   
   // Optionally set user agent  
   auditudeSettings.setUserAgent("yourUserAgent"); 
   
   Metadata targetingParameters = new Metadata(); 
   targetingParameters.setValue("desired_param", "desired_value"); 
   auditudeSettings.setTargetingParameters(targetingParameters);
   ```

   >[!TIP]
   >
   >De media-id wordt door TVSDK gebruikt als een tekenreeks, die wordt omgezet in een md5-waarde en wordt gebruikt voor de `u` waarde in het verzoek Primetime en beslissings-URL. Bijvoorbeeld:
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Maak een `MediaResource` instantie met de URL van de mediastream en de eerder gemaakte metagegevens voor advertenties.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Laad het `MediaResource` object via de `MediaPlayer.replaceCurrentResource` methode.

   Het `MediaPlayer` begin ladend en verwerkt media stroommanifest.

1. Wanneer de `MediaPlayer` overgangen naar de INITIALIZED status, krijg de eigenschappen van de media stroom in de vorm van een `MediaPlayerItem` instantie door de `MediaPlayer.CurrentItem` methode.
1. (Optioneel) Vraag de `MediaPlayerItem` instantie om na te gaan of de stream live is, ongeacht of deze alternatieve audiotracks heeft of dat de stream is beveiligd.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bel `MediaPlayer.prepareToPlay` om de advertentieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, gaat de `MediaPlayer` overgang naar de `PREPARED` status.
1. Bel `MediaPlayer.play` om het afspelen te starten.
TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.
