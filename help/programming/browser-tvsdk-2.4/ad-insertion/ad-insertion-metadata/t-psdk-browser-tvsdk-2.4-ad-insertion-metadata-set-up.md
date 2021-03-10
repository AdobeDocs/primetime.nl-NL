---
description: Gebruik de hulpklasse AuditudeSettings om Adobe Primetime- en beslissingsmetagegevens in te stellen.
title: Metagegevens instellen en invoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Metagegevens instellen en invoegen{#set-up-ad-insertion-metadata}

Gebruik de hulpklasse AuditudeSettings om Adobe Primetime- en beslissingsmetagegevens in te stellen.

>[!TIP]
>
>Adobe Primetime en het besluit stond voorheen bekend als Auditude.

1. Stel de instantie `AuditudeSettings` samen.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Stel de Adobe Primetime- en beslissingsmedia-id, zoneID, domain en de optionele parameters voor toewijzen in.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Maak een `MediaResource`-instantie met de URL van de mediastream en de eerder gemaakte advertentiemetagegevens.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Laad het object `MediaResource` via de methode `MediaPlayer.replaceCurrentResource(resource)`.

   Met `MediaPlayer` wordt het mediabream geladen en verwerkt.

1. Wanneer de `MediaPlayer` naar de geINITIALISEERDE status overgaat, krijg de eigenschappen van de media stroom in de vorm van een `MediaPlayerItem` instantie door het `MediaPlayer.CurrentItem` attribuut.
1. (Optioneel) Vraag de instantie `MediaPlayerItem` om te zien of de stream live is, ongeacht of deze alternatieve audiotracks heeft.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bel `MediaPlayer.prepareToPlay` om de advertentieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, gaat `  MediaPlayer ` over naar de status PREPARED.
1. Roep `MediaPlayer.play` aan om het afspelen te starten.
Browser-TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.
