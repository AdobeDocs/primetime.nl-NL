---
description: De volgende wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# Wijzigingen in API voor verwijderen en vervangen toevoegen{#ad-deletion-and-replacement-api-changes}

De volgende wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.

**Nieuwe API&#39;s**

* `PTTimeRangeCollection` is een klasse public die een vooraf gedefinieerde set bereiken en een type definieert:

   * `property PTTimeRangeCollectionType type` Hiermee wordt het type tijdbereik aangegeven.
   * `property NSArray* ranges` wordt gebruikt om de tijdwaaiers te plaatsen.

      Het verwachte type objecten in de array zijn `PTReplacementTimeRange` of `CMTimeRange`.

      >[!TIP]
      >
      >Alle objecten van de array moeten van hetzelfde type zijn.

   * `PTTimeRangeCollectionType` is een opsomming die het gedrag definieert voor de bereiken die zijn gedefinieerd in het dialoogvenster `PTTimeRangeCollection`:

      * `PTTimeRangeCollectionTypeMarkRanges`: Het type van de bereiken is *Mark*. De bereiken worden gebruikt om de waaiers in de inhoud als Advertentie te merken.

      * `PTTimeRangeCollectionTypeDeleteRanges`: Het type van de bereiken is Delete. De gedefinieerde bereiken worden voor het invoegen uit de hoofdinhoud verwijderd.
      * `PTTimeRangeCollectionTypeReplaceRanges`: Het type van de bereiken is Vervangen. De gedefinieerde bereiken worden vanaf de hoofdregel vervangen door Advertenties (de modus voor Ad-signalering is ingesteld op `PTAdSignalingModeCustomTimeRanges`).

* `PTReplacementTimeRange` - Nieuwe klasse public die één bereik van de klasse `PTTimeRangeCollection`:

   * `property CMTimeRange range` - Definieert het begin en de duur van het bereik.
   * `property long replacementDuration` - Indien het type van de `TimeRangeCollection` is `PTTimeRangeCollectionTypeReplaceRanges`de `replacementDuration` wordt gebruikt om een plaatsingskans (en invoeging) te maken met een duur van `replacementDuration`. Als de `replacementDuration` niet is ingesteld, bepaalt de advertentieserver de duur en het aantal advertenties voor die plaatsingsmogelijkheid.

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges` - Een nieuw type van `PTAdSignalingMode`. Deze modus wordt gebruikt in combinatie met de `PTTimeRangeCollection` met type `PTTimeRangeCollectionReplace` voor toevoegen op basis van het vervangingsbereik.

* `PTAdMetadata`:

   * `property PTTimeRangeCollection* timeRangeCollection` - Voor het instellen van de tijdbereiken die worden gebruikt in de reeks mark/delete/replace in de afspeelinhoud.

* Waarschuwingslogboeken:

   * `UNDEFINED_TIME_RANGES`

      * Type - Waarschuwing
      * Beschrijving - De ad-signaalmodus wordt gedefinieerd als aangepaste bereiken, maar de aangepaste bereiken worden niet gedefinieerd.
   * `INVALID_TIME_RANGES`

      * Type - Waarschuwing
      * Beschrijving - Een of meer tijdbereiken zijn ongeldig en worden genegeerd of gewijzigd.


**Verouderde API&#39;s**

* `PTAdMetadata`:

   * `property NSArray* externalAdRanges` - Deze eigenschap werd eerder gebruikt om C3-bereiken voor markering te definiëren. Het is nu afgekeurd, omdat deze bereiken zijn ingesteld via `PTTimeRangeCollection`.

