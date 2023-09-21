---
description: Gebruik de hulpklasse AuditudeSettings om Adobe Primetime- en beslissingsmetagegevens in te stellen.
title: Metagegevens instellen en invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Metagegevens instellen en invoegen{#set-up-ad-insertion-metadata}

Gebruik de hulpklasse AuditudeSettings om Adobe Primetime- en beslissingsmetagegevens in te stellen.

>[!TIP]
>
>Adobe Primetime en het besluit stond voorheen bekend als Auditude.

1. De `AuditudeSettings` -instantie.

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Stel de Adobe Primetime- en beslissingsmedia-id, zoneID, domain en de optionele parameters voor toewijzen in.

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. Een `MediaResource` door de URL van de mediastream en de eerder gemaakte advertentiemetagegevens te gebruiken.

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. Laad de `MediaResource` door het `MediaPlayer.replaceCurrentResource(resource)` methode.

   De `MediaPlayer` start met het laden en verwerken van het mediastroommanifest.

1. Wanneer de `MediaPlayer` overgangen naar de status INITIALIZED, krijg de kenmerken van de mediastream in de vorm van een `MediaPlayerItem` door de `MediaPlayer.CurrentItem` kenmerk.
1. (Optioneel) Zoek naar de `MediaPlayerItem` -instantie om te zien of de stream live is, ongeacht of deze alternatieve audiotracks heeft.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bellen `MediaPlayer.prepareToPlay` om de publicatieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, wordt het `  MediaPlayer ` overgangen naar de status PREPARED.
1. Bellen `MediaPlayer.play` om het afspelen te starten.
Browser-TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.
