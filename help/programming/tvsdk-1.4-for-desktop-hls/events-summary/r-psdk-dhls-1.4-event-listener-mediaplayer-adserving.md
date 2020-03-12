---
description: TVSDK verzendt ad-serving-gebeurtenissen als reactie op getimede metagegevensbewerkingen.
seo-description: TVSDK verzendt ad-serving-gebeurtenissen als reactie op getimede metagegevensbewerkingen.
seo-title: Gebeurtenissen van metagegevens met tijdslimiet toevoegen
title: Gebeurtenissen van metagegevens met tijdslimiet toevoegen
uuid: fd50a937-0c9b-4c47-acb2-1ffc0592ad54
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Gebeurtenissen van metagegevens met tijdslimiet toevoegen{#ad-serving-timed-metadata-events}

TVSDK verzendt ad-serving-gebeurtenissen als reactie op getimede metagegevensbewerkingen.

Om op de hoogte te worden gebracht van al dergelijke gerelateerde gebeurtenissen, registreert u gebeurtenislisteners bij het `MediaPlayer` object voor de volgende gebeurtenissen.

| Gebeurtenis | Betekenis |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | Er zijn metagegevens met een ID3-tijdinstelling verwerkt. |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | Er zijn metagegevens met een tijdslimiet verwerkt en er is geen mogelijkheid gedetecteerd. |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | Er zijn getimede metagegevens beschikbaar en er is geen gelegenheid gedetecteerd. |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | Er zijn getimede metagegevens verwerkt en er is geen gelegenheid gedetecteerd in het achtergrondmanifest. |