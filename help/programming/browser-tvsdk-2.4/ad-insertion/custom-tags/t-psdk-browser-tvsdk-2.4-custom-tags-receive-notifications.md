---
description: Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.
title: Listeners toevoegen voor meldingen met tijdmetagegevens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# Listeners toevoegen voor meldingen met tijdmetagegevens{#add-listeners-for-timed-metadata-notifications}

Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.

Wanneer een nieuwe `TimedMetadata` -object wordt gemaakt, wordt de MediaPlayer verzonden `AdobePSDK.TimedMetadataEvent`.

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

ID3-metagegevens worden via hetzelfde verzonden `Events.TimedMetadataEvent`. U kunt de `timedMetadata.type` eigenschap om onderscheid te maken tussen TAG en ID3.
