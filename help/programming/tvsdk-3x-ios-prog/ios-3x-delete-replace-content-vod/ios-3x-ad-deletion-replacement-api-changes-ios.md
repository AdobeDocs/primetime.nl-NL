---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-title: Wijzigingen in API voor verwijderen en vervangen toevoegen
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
uuid: 3689d31f-4feb-4ea5-ac49-ef2e71472f4b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Wijzigingen in API voor verwijderen en vervangen toevoegen {#ad-deletion-and-replacement-api-changes}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

<!--<a id="section_7A90BFE99F1A4D908D6DDB0B49FA1199"></a>-->

De volgende wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.

**Nieuwe API&#39;s**

* `PTTimeRangeCollection` is een klasse public die een vooraf gedefinieerde set bereiken en een type definieert:

   * `property PTTimeRangeCollectionType type` Hiermee wordt het type tijdbereik aangegeven.
   * `property NSArray* ranges` wordt gebruikt om de tijdwaaiers te plaatsen.

      Het verwachte type objecten in de array is `PTReplacementTimeRange` of `CMTimeRange`.

      >[!TIP]
      >
      >Alle objecten van de array moeten van hetzelfde type zijn.

   * `PTTimeRangeCollectionType` is een opsomming die het gedrag definieert voor de bereiken die in het `PTTimeRangeCollection`volgende worden gedefinieerd:

      * `PTTimeRangeCollectionTypeMarkRanges`: Het type van de bereiken is *Mark*. De bereiken worden gebruikt om de waaiers in de inhoud als Advertentie te merken.

      * `PTTimeRangeCollectionTypeDeleteRanges`: Het type van de bereiken is Delete. De gedefinieerde bereiken worden voor het invoegen uit de hoofdinhoud verwijderd.
      * `PTTimeRangeCollectionTypeReplaceRanges`: Het type van de bereiken is Vervangen. De gedefinieerde bereiken worden vanaf het hoofdvenster vervangen door Advertenties (de modus voor Ad-signalering is ingesteld op `PTAdSignalingModeCustomTimeRanges`).

* `PTReplacementTimeRange` - Nieuwe klasse public die één bereik van de `PTTimeRangeCollection`:

   * `property CMTimeRange range` - Definieert het begin en de duur van het bereik.
   * `property long replacementDuration` - Als het type van `TimeRangeCollection` is `PTTimeRangeCollectionTypeReplaceRanges`, `replacementDuration` wordt gebruikt om een plaatsingskans (en toevoeging) met een duur van `replacementDuration`. te creëren. Als de advertentieserver niet `replacementDuration` is ingesteld, bepaalt de advertentieserver de duur en het aantal advertenties voor die plaatsingsmogelijkheid.

* `PTAdSignalingMode`:

   * `PTAdSignalingModeCustomTimeRanges` - Er is een nieuw type `PTAdSignalingMode`toegevoegd. Deze modus wordt gebruikt in combinatie met het `PTTimeRangeCollection` type voor invoeging `PTTimeRangeCollectionReplace` op basis van de vervangingsbereiken.

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

   * `property NSArray* externalAdRanges` - Deze eigenschap werd eerder gebruikt om C3-bereiken voor markering te definiëren. Het is nu afgekeurd, aangezien deze bereiken via worden ingesteld `PTTimeRangeCollection`.