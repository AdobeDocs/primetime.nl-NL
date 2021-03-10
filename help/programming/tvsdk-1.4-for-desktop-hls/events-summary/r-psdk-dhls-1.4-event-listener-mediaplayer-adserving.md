---
description: TVSDK verzendt ad-serving-gebeurtenissen als reactie op getimede metagegevensbewerkingen.
title: Gebeurtenissen van metagegevens met tijdslimiet toevoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Gebeurtenissen voor metagegevens via serving/timed toevoegen{#ad-serving-timed-metadata-events}

TVSDK verzendt ad-serving-gebeurtenissen als reactie op getimede metagegevensbewerkingen.

Om op de hoogte te worden gebracht van al dergelijke gerelateerde gebeurtenissen, registreert u gebeurtenislisteners bij het `MediaPlayer`-object voor de volgende gebeurtenissen.

| Gebeurtenis | Betekenis |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Er zijn metagegevens met een ID3-tijdinstelling verwerkt. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Er zijn metagegevens met een tijdslimiet verwerkt en er is geen mogelijkheid gedetecteerd. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Er zijn getimede metagegevens beschikbaar en er is geen gelegenheid gedetecteerd. |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Er zijn getimede metagegevens verwerkt en er is geen gelegenheid gedetecteerd in het achtergrondmanifest. |