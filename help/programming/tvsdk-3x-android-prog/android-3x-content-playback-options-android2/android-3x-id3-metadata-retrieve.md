---
description: ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. TVSDK detecteert ID3-tags op het segmentniveau van de transportstream (TS) in HLS-streams en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.
title: ID3-tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# ID3-tags {#id-tags}

ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. TVSDK detecteert ID3-tags op het segmentniveau van de transportstream (TS) in HLS-streams en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.

>[!IMPORTANT]
>
>TVSDK herkent ID3-metagegevens (versie 2.3.0 of 2.4.0) in audio- (AAC) en videostreams (H.264) in een van de mogelijke coderingen (ASCII, UTF8, UTF16-BE of UTF16-LE). ID3-tags worden genegeerd die zich niet in een van de herkende versies of indelingen bevinden. Niet-opgegeven codering wordt behandeld als UTF8.

Wanneer TVSDK ID3-metagegevens detecteert, wordt een melding met de volgende gegevens weergegeven:

* TYPE = ID3
* NAME = ID3

1. Implementeer een gebeurtenislistener voor `MediaPlayer.TimedMetadataEventListener#onTimedMetadata(TimeMetadata timeMetadata)` en registreer deze bij het object `MediaPlayer`.

   TVSDK roept deze listener aan wanneer deze `ID3` metagegevens detecteert.

   >[!TIP]
   >
   >Aangepaste cues en cues gebruiken dezelfde gebeurtenis `onTimedMetadata` om de detectie van een nieuwe tag aan te geven. Dit mag geen verwarring veroorzaken omdat aangepaste ad-cues worden gedetecteerd op manifestniveau en ID3-tags zijn ingesloten in de stream. Zie [Aangepaste tags](../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/custom-tags-configure/android-3x-custom-tags-configure.md) voor meer informatie.

1. Haal de metagegevens op.

   ```java
   @Override 
    public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               byte[] value = metadata.getByteArray(key); 
           } 
       } 
   }
   ```
