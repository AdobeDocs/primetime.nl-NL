---
description: Met de hulpklasse AuditudeSettings stelt u Adobe Primetime- en beslissingsmetagegevens in.
seo-description: Met de hulpklasse AuditudeSettings stelt u Adobe Primetime- en beslissingsmetagegevens in.
seo-title: Metagegevens instellen en invoegen
title: Metagegevens instellen en invoegen
uuid: fc37e0ae-6acf-4a78-a468-f7b5b123b45e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Metagegevens instellen en invoegen{#set-up-ad-insertion-metadata}

Met de hulpklasse AuditudeSettings stelt u Adobe Primetime- en beslissingsmetagegevens in.

>[!TIP]
>
>Adobe Primetime en het besluit was eerder bekend als Auditude.

1. Maak de `AuditudeSettings` instantie.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Stel de Adobe Primetime- en beslissingsmedia-id, zoneID, domain en de optionele doelparameters in.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Maak een `MediaResource` instantie met de URL van de mediastream en de eerder gemaakte metagegevens voor advertenties.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Laad het `MediaResource` object via de `MediaPlayer.replaceCurrentResource(resource)` methode.

   Het `MediaPlayer` begin ladend en verwerkt media stroommanifest.

1. Wanneer de `MediaPlayer` overgangen naar de INITIALIZED status, krijg de eigenschappen van de media stroom in de vorm van een `MediaPlayerItem` instantie door het `MediaPlayer.CurrentItem` attribuut.
1. (Optioneel) Vraag de `MediaPlayerItem` instantie om na te gaan of de stream live is, ongeacht of er alternatieve audiotracks zijn.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bel `MediaPlayer.prepareToPlay` om de advertentieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, gaat de `  MediaPlayer ` overgang naar de status PREPARED.
1. Bel `MediaPlayer.play` om het afspelen te starten.
Browser-TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.
