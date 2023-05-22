---
description: Registreer de juiste gebeurtenislistener(s) om meldingen over tags in het manifest te ontvangen.
title: Listeners toevoegen voor meldingen van getimede metagegevens
exl-id: 1df8a4fc-8368-4a80-8f8b-00c1207e6602
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Listeners toevoegen voor meldingen van getimede metagegevens{#add-listeners-for-timed-metadata-notifications}

Registreer de juiste gebeurtenislistener(s) om meldingen over tags in het manifest te ontvangen.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `MediaPlayerItemEvent.ITEM_CREATED`: De eerste lijst van `TimedMetadata` objecten zijn beschikbaar na de `MediaPlayerItem` wordt gemaakt.

   Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `MediaPlayerItemEvent.ITEM_UPDATED`: Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het bijgewerkte manifest, zodat aanvullende `TimedMetadata` objecten kunnen worden toegevoegd aan de `MediaPlayerItem.timedMetadata` eigenschap.

   Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`: Elke keer een nieuwe `TimedMetadata` -object wordt gemaakt, wordt deze gebeurtenis verzonden door de MediaPlayer.

   Deze gebeurtenis wordt niet verzonden voor de `TimedMetadata` object dat tijdens de initialisatiefase is gemaakt.

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

ID3-metagegevens worden via hetzelfde verzonden `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`. Dit mag echter geen verwarring veroorzaken, omdat u de objecten TimedMetadata kunt gebruiken `type` eigenschap om onderscheid te maken tussen TAG en ID3. Voor meer informatie over ID3-tags raadpleegt u [ID3-tags](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md).
