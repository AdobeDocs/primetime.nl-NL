---
description: Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.
title: Listeners toevoegen voor meldingen van getimede metagegevens
exl-id: e4be34b6-0f29-45b8-a089-b79b41daeada
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Listeners toevoegen voor meldingen van getimede metagegevens {#add-listeners-for-timed-metadata-notifications}

Als u meldingen over tags in het manifest wilt ontvangen, moet u de juiste gebeurtenislisteners implementeren.

U kunt vastgestelde meta-gegevens controleren door te luisteren naar `onTimedMetadata`, die uw toepassing op de hoogte stelt van verwante activiteiten. Telkens wanneer een unieke geabonneerde tag wordt geïdentificeerd tijdens het parseren van de inhoud, bereidt TVSDK een nieuwe tag voor `TimedMetadata` en verzendt deze gebeurtenis. Het object bevat de naam van de tag waarop u zich hebt geabonneerd, de lokale tijd tijdens het afspelen waar deze tag wordt weergegeven en andere gegevens.

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

ID3-metagegevens gebruiken hetzelfde `onTimedMetadata` listener die de aanwezigheid van een ID3-tag aangeeft. Dit mag echter geen verwarring veroorzaken, omdat u de `TimedMetadata` `type` eigenschap om onderscheid te maken tussen TAG en ID3. Voor meer informatie over ID3-tags raadpleegt u [ID3-tags](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md).
