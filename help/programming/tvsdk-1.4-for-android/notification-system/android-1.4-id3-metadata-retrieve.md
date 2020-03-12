---
description: ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. TVSDK detecteert ID3-tags op het segmentniveau van de transportstream (TS) in HLS-streams en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.
seo-description: ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. TVSDK detecteert ID3-tags op het segmentniveau van de transportstream (TS) in HLS-streams en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.
seo-title: ID3-tags
title: ID3-tags
uuid: 5e5c5f89-7653-47c1-b9c1-6b9b9b1f8d73
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ID3-tags {#id-tags}

ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. TVSDK detecteert ID3-tags op het segmentniveau van de transportstream (TS) in HLS-streams en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.

>[!IMPORTANT]
>
>TVSDK herkent ID3-metagegevens (versie 2.3.0 of 2.4.0) in audio- (AAC) en videostreams (H.264) in een van de mogelijke coderingen (ASCII, UTF8, UTF16-BE of UTF16-LE). ID3-tags worden genegeerd die zich niet in een van de herkende versies of indelingen bevinden. Niet-opgegeven codering wordt behandeld als UTF8.

Wanneer TVSDK ID3-metagegevens detecteert, wordt een melding met de volgende gegevens weergegeven:

* InfoCode = 303007
* TYPE = ID3
* NAME = niet aanwezig
* ID = 0

1. Implementeer een gebeurtenislistener voor `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` en registreer deze bij het `MediaPlayer` object.

   TVSDK roept deze listener aan wanneer deze ID3-metagegevens detecteert.

   >[!NOTE]
   >
   >Aangepaste cues en cues gebruiken dezelfde `onTimedMetadata` gebeurtenis om de detectie van een nieuwe tag aan te geven. Dit mag geen verwarring veroorzaken omdat aangepaste ad-cues worden gedetecteerd op manifestniveau en ID3-tags zijn ingesloten in de stream. Voor meer informatie, zie douane-markeringen-vormen.

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
               String value = metadata.getValue(key); 
           } 
       } 
   }
   ```

