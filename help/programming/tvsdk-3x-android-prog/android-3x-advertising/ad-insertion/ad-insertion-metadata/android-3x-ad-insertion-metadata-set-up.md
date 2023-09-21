---
description: Met de hulpklasse AuditudeSettings, die de klasse MetadataNode uitbreidt, kunt u Adobe Primetime- en beslissingsmetagegevens instellen.
title: Metagegevens instellen en invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Metagegevens instellen en invoegen {#set-up-ad-insertion-metadata}

De hulpklasse gebruiken `AuditudeSettings`, die de `MetadataNode` -klasse, om Adobe Primetime en beslissingsmetagegevens in te stellen.

>[!TIP]
>
>Adobe Primetime en de beslissing stond voorheen bekend als Auditude.

Metagegevens over reclame bevinden zich in de `MediaResource.Metadata` eigenschap. Wanneer u begint met het afspelen van een nieuwe video, is uw toepassing verantwoordelijk voor het instellen van de juiste metagegevens voor advertenties.

1. De `AuditudeSettings` -instantie.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. De Adobe Primetime en de beslissing instellen `mediaID`, `zoneID`, `<ph conkeyref="phrases/primetime-sdk-name"/>`en de optionele doelparameters.

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
   >De media-id wordt door TVSDK gebruikt als een tekenreeks, die wordt omgezet in een md5-waarde en wordt gebruikt voor de `u` waarde in het Primetime- en beslissings-URL-verzoek. Bijvoorbeeld:
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Een `MediaResource` door de URL van de mediastream en de eerder gemaakte advertentiemetagegevens te gebruiken.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Laad de `MediaResource` door het `MediaPlayer.replaceCurrentResource` methode.

   De `MediaPlayer` start met het laden en verwerken van het mediastroommanifest.

1. Wanneer de `MediaPlayer` overgangen naar de status INITIALIZED, krijg de kenmerken van de mediastream in de vorm van een `MediaPlayerItem` door de `MediaPlayer.CurrentItem` methode.
1. (Optioneel) Zoek naar de `MediaPlayerItem` -instantie om te zien of de stream live is, ongeacht of de stream alternatieve audiotracks heeft of dat de stream beveiligd is.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bellen `MediaPlayer.prepareToPlay` om de publicatieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, wordt het `MediaPlayer` overgangen naar de `PREPARED` status.
1. Bellen `MediaPlayer.play` om het afspelen te starten.
TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.
