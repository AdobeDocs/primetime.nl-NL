---
description: Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.
seo-description: Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.
seo-title: Listeners toevoegen voor meldingen van getimede metagegevens
title: Listeners toevoegen voor meldingen van getimede metagegevens
uuid: c82c5549-0ab6-4343-a766-5176e784d4cb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Listeners toevoegen voor meldingen van getimede metagegevens{#add-listeners-for-timed-metadata-notifications}

Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.

Wanneer een nieuw `TimedMetadata` object wordt gemaakt, verzendt de MediaPlayer `AdobePSDK.TimedMetadataEvent`.

1. Voer de aangewezen luisteraars uit.

   ```js
   function onTimedMetadataEvent(event) { 
       var timedMetadata = event.timedMetadata; 
       // process the timed metadata collection 
       } 
   ```

1. Registreer de gebeurtenislisteners.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE, onTimedMetadataEvent);
   ```

ID3-metagegevens worden op dezelfde manier verzonden `Events.TimedMetadataEvent`. U kunt de `timedMetadata.type` eigenschap gebruiken om onderscheid te maken tussen TAG en ID3.

