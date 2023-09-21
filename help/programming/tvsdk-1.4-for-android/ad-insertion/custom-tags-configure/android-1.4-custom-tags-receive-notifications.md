---
description: Implementeer de juiste gebeurtenislistener(s) om meldingen over tags in het manifest te ontvangen.
title: Listeners toevoegen voor meldingen van getimede metagegevens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Listeners toevoegen voor meldingen van getimede metagegevens {#add-listeners-for-timed-metadata-notifications}

Implementeer de juiste gebeurtenislistener(s) om meldingen over tags in het manifest te ontvangen.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `onTimedMetadata`: Telkens wanneer een unieke geabonneerde tag wordt geïdentificeerd tijdens het parseren van de inhoud, bereidt TVSDK een nieuwe tag voor `TimedMetadata` en verzendt deze gebeurtenis.

  Het object bevat de naam van de tag waarop u zich hebt geabonneerd, de lokale tijd tijdens het afspelen waar deze tag wordt weergegeven en andere gegevens.

  Luister naar gebeurtenissen.

  ```java
  private final TimedMetadataEventListener timedMetadataEventListener =  
    new TimedMetadataEventListener() { 
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
          } else if (_mediaPlayer.getPlaybackRange() !=  
                     null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
              displayRanges(); 
          } 
      } 
  }; 
  ```

ID3-metagegevens gebruiken dezelfde onTimedMetadata-listener om de aanwezigheid van een ID3-tag aan te geven. Dit mag echter geen verwarring veroorzaken, omdat u een `TimedMetadata` object `type` eigenschap voor onderscheid tussen TAG en ID3. Zie voor meer informatie over ID3-tags [ID3-tags](../../../tvsdk-1.4-for-android/notification-system/android-1.4-id3-metadata-retrieve.md).
