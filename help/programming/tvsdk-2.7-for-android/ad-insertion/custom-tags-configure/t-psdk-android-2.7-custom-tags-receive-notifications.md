---
description: Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.
seo-description: Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.
seo-title: Listeners toevoegen voor meldingen van getimede metagegevens
title: Listeners toevoegen voor meldingen van getimede metagegevens
uuid: 336882e7-e2d8-49b8-a23d-f236c7e6a594
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Listeners toevoegen voor meldingen van getimede metagegevens {#add-listeners-for-timed-metadata-notifications}

Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.

U kunt getimede metagegevens controleren door te luisteren naar `onTimedMetadata`de desbetreffende activiteit, die uw toepassing op de hoogte stelt van deze activiteit. Telkens wanneer een unieke geabonneerde tag wordt geïdentificeerd tijdens het parseren van de inhoud, bereidt TVSDK een nieuw `TimedMetadata` object voor en verzendt deze gebeurtenis. Het object bevat de naam van de tag waarop u zich hebt geabonneerd, de lokale tijd tijdens het afspelen waar deze tag wordt weergegeven en andere gegevens.

1. Luister naar gebeurtenissen.

   ```java
   private final TimedMetadataEventListener timedMetadataEventListener = new TimedMetadataEventListener() { 
       @Override 
       public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { 
           TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata(); 
   
           TimedMetadata.Type type = timedMetadata.getType(); 
           if (type.equals(TimedMetadata.Type.ID3)){ 
               Metadata metadata = timedMetadata.getMetadata(); 
               Set<String> keys = metadata.keySet(); 
               for (String key : keys) { 
                   String value = metadata.getValue(key); 
               } 
           } else if (_mediaPlayer.getPlaybackRange() != null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
               displayRanges(); 
           } 
       } 
   }; 
   ```

ID3-metagegevens gebruiken dezelfde `onTimedMetadata` listener om de aanwezigheid van een ID3-tag aan te geven. Dit zou geen verwarring, echter moeten veroorzaken, omdat u het `TimedMetadata` `type` bezit kunt gebruiken om tussen TAG en ID3 te onderscheiden. Zie [ID3-tags](../../content-playback-options/t-psdk-android-2.7-id3-metadata-retrieve.md)voor meer informatie over ID3-tags.