---
description: Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.
title: Listeners toevoegen voor meldingen van getimede metagegevens
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---


# Listeners toevoegen voor meldingen met tijdmetagegevens{#add-listeners-for-timed-metadata-notifications}

Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.

Wanneer een nieuw `TimedMetadata` voorwerp wordt gecreeerd, verzendt MediaPlayer `AdobePSDK.TimedMetadataEvent`.

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

ID3-metagegevens worden via dezelfde `Events.TimedMetadataEvent` verzonden. Met de eigenschap `timedMetadata.type` kunt u onderscheid maken tussen TAG en ID3.

