---
description: Registreer de juiste gebeurtenislistener(s) om meldingen over tags in het manifest te ontvangen.
seo-description: Registreer de juiste gebeurtenislistener(s) om meldingen over tags in het manifest te ontvangen.
seo-title: Listeners toevoegen voor meldingen van getimede metagegevens
title: Listeners toevoegen voor meldingen van getimede metagegevens
uuid: 419f4204-e3c3-4608-beb4-4cd259c8474d
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Listeners toevoegen voor meldingen van getimede metagegevens{#add-listeners-for-timed-metadata-notifications}

Registreer de juiste gebeurtenislistener(s) om meldingen over tags in het manifest te ontvangen.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst met  `TimedMetadata` objecten is beschikbaar nadat de objecten  `MediaPlayerItem` zijn gemaakt.

   Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het manifest, zodat aanvullende  `TimedMetadata` objecten aan de  `MediaPlayerItem.timedMetadata` eigenschap kunnen worden toegevoegd.

   Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Elke keer dat een nieuw  `TimedMetadata` object wordt gemaakt, wordt deze gebeurtenis verzonden door de MediaPlayer.

   Deze gebeurtenis wordt niet verzonden voor het `TimedMetadata`-object dat tijdens de initialisatiefase is gemaakt.

1. Voer de aangewezen luisteraars uit.

   ```
   private function onItemCreated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onItemUpdated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onTimedMetadataAvailable(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       // process timed metadata 
   }
   ```

1. Registreer de gebeurtenislisteners.

   ```
   player.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
   player.addEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE,  
                           onTimedMetadataAvailable);
   ```

ID3-metagegevens worden via dezelfde `TimedMetadataEvent.TIMED_METADATA_AVAILABLE` verzonden. Dit zou geen verwarring, echter moeten veroorzaken, omdat u het `type` bezit van een voorwerp TimedMetadata kunt gebruiken om tussen TAG en ID3 te onderscheiden. Zie [ID3-tags](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md) voor meer informatie over ID3-tags.