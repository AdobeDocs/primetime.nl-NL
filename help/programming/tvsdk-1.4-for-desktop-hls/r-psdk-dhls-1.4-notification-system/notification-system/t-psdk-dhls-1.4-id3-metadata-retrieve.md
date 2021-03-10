---
description: ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. Hiermee worden ID3-tags op het niveau van het transportstreamsegment (TS) in HLS-streams gedetecteerd en wordt een gebeurtenis verzonden. De toepassing kan gegevens uit de tag extraheren.
title: ID3-tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# ID3-tags{#id-tags}

ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. Hiermee worden ID3-tags op het niveau van het transportstreamsegment (TS) in HLS-streams gedetecteerd en wordt een gebeurtenis verzonden. De toepassing kan gegevens uit de tag extraheren.

>[!IMPORTANT]
>
>TVSDK herkent ID3-metagegevens (versie 2.3.0 of 2.4.0) in audio- (AAC) en videostreams (H.264) in een van de mogelijke coderingen (ASCII, UTF8, UTF16-BE of UTF16-LE). ID3-tags worden genegeerd die zich niet in een van de herkende versies of indelingen bevinden. Niet-opgegeven codering wordt behandeld als UTF8.

Wanneer TVSDK ID3-metagegevens detecteert, wordt een melding met de volgende gegevens weergegeven:

* InfoCode = 303007
* TYPE = ID3
* NAME = niet aanwezig
* ID = 0

1. Implementeer een gebeurtenislistener voor `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED` en registreer deze bij het object `MediaPlayer`.

   TVSDK roept deze listener aan wanneer deze ID3-metagegevens detecteert.

   >[!NOTE]
   >
   >Aangepaste cues en cues gebruiken dezelfde gebeurtenis `onTimedMetadata` om de detectie van een nieuwe tag aan te geven. Dit mag geen verwarring veroorzaken omdat aangepaste ad-cues worden gedetecteerd op manifestniveau en ID3-tags zijn ingesloten in de stream. Voor meer informatie, zie douane-markeringen-vormen.

1. Haal de metagegevens op.

   ```
   private function onID3Metadata(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       var metadata:Metadata = timedMetadata.metadata; 
       var keys:Vector.<String> = metadata.keySet(); 
       for (var i:int = keys.length - 1; i >= 0; --i) { 
           var value:ByteArray = metadata.getByteArray(keys[i]); 
           _logger.info("#onTimedMetadata Detected dictionary data key: [{0}],  
                        value: [{1}] of length {2} bytes at time [{3}].",  
                        keys[i],  
                        value.toString(),  
                        value.length,  
                        event.timedMetadata.time); 
       } 
   } 
   ```

