---
description: Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.
title: Listeners toevoegen voor meldingen van getimede metagegevens
exl-id: eea2505f-595c-4bbe-9b68-ae395943c888
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# Listeners toevoegen voor meldingen van getimede metagegevens{#add-listeners-for-timed-metadata-notifications}

Luister naar AdobePSDK.TimedMetadataEvent om meldingen over tags in het manifest te ontvangen.

Wanneer een nieuwe `TimedMetadata` -object wordt gemaakt, de MediaPlayer verzendt `AdobePSDK.TimedMetadataEvent`.

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
