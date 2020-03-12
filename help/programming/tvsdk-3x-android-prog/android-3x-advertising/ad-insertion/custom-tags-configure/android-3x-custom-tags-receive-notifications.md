---
description: Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.
seo-description: Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.
seo-title: Listeners toevoegen voor meldingen van getimede metagegevens
title: Listeners toevoegen voor meldingen van getimede metagegevens
uuid: bb996b4a-282e-4321-a9e9-513f0df45b70
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Listeners toevoegen voor meldingen van getimede metagegevens {#add-listeners-for-timed-metadata-notifications}

Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.

U kunt getimede metagegevens controleren door te luisteren naar `onTimedMetadata`de desbetreffende activiteit, die uw toepassing op de hoogte stelt van deze activiteit. Telkens wanneer een unieke geabonneerde tag wordt geïdentificeerd tijdens het parseren van de inhoud, bereidt TVSDK een nieuw `TimedMetadata` object voor en verzendt deze gebeurtenis. Het object bevat de naam van de tag waarop u zich hebt geabonneerd, de lokale tijd tijdens het afspelen waar deze tag wordt weergegeven en andere gegevens.

Luister naar gebeurtenissen.

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

ID3-metagegevens gebruiken dezelfde `onTimedMetadata` listener om de aanwezigheid van een ID3-tag aan te geven. Dit zou geen verwarring, echter moeten veroorzaken, omdat u het `TimedMetadata` `type` bezit kunt gebruiken om tussen TAG en ID3 te onderscheiden. Zie [ID3-tags](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md)voor meer informatie over ID3-tags.