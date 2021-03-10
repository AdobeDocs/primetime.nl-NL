---
description: Met de hulpklasse AuditudeSettings, die de klasse MetadataNode uitbreidt, kunt u Adobe Primetime- en beslissingsmetagegevens instellen.
title: Metagegevens instellen en invoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Metagegevens instellen en invoegen {#set-up-ad-insertion-metadata}

Met de hulpklasse AuditudeSettings, die de klasse MetadataNode uitbreidt, kunt u Adobe Primetime- en beslissingsmetagegevens instellen.

>[!TIP]
>
>Adobe Primetime en de beslissing stond voorheen bekend als Auditude.

Metagegevens voor reclame bevinden zich in de eigenschap `MediaResource.Metadata`. Wanneer u begint met het afspelen van een nieuwe video, is uw toepassing verantwoordelijk voor het instellen van de juiste metagegevens voor advertenties.

1. Stel de instantie `AuditudeSettings` samen.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Stel de Adobe Primetime en de beslissing `mediaID`, `zoneID`, `domain` en de optionele parameters voor het toewijzen van doelen in.

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
   >De media-id wordt door TVSDK gebruikt als een tekenreeks, die wordt omgezet in een md5-waarde en wordt gebruikt voor de waarde `u` in het URL-verzoek voor primetime en besluitvorming. Bijvoorbeeld:
   >
   >
   ```
   >https://ad.auditude.com/adserver?
   >u=c76d04ee31c91c4ce5c8cee41006c97d
   >   &z=114100 
   >   &l=20150206141527 
   >   &of=1.4 
   >   &tm=15 
   >   &g=1000002
   >```

1. Maak een `MediaResource`-instantie met de URL van de mediastream en de eerder gemaakte advertentiemetagegevens.

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. Laad het object `MediaResource` via de methode `MediaPlayer.replaceCurrentResource`.

   Met `MediaPlayer` wordt het mediabream geladen en verwerkt.

1. Wanneer de `MediaPlayer` naar de `INITIALIZED` status overgaat, krijg de eigenschappen van de media stroom in de vorm van een `MediaPlayerItem` instantie door de `MediaPlayer.CurrentItem` methode.
1. (Optioneel) Vraag de instantie `MediaPlayerItem` om te zien of de stream live is, ongeacht of deze alternatieve audiotracks heeft of of de stream is beveiligd.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bel `MediaPlayer.prepareToPlay` om de advertentieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, gaat `MediaPlayer` naar de status `PREPARED`.
1. Roep `MediaPlayer.play` aan om het afspelen te starten.

TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.
