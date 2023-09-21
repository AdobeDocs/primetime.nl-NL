---
description: Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Wijzigingen in API voor verwijderen en vervangen toevoegen {#ad-deletion-and-replacement-api-changes}

Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.

* `AdSignalingMode` Toegevoegd `CUSTOM_RANGES` signaalmodus.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Set `AdSignalingMode.CUSTOM_RANGES` als de metagegevens reeksen voor het vervangen van reeksen bevatten.

* `PlacementType` Toegevoegd `CUSTOM_RANGE` type.

* `PlacementMode`

   * Toegevoegd `DELETE` -modus.
   * Toegevoegd `MARK` mode
   * Toegevoegd `FreeReplace` modus - Deze modus heeft een duur maar is een zuivere invoeging

* `TimeRange` Niet langer een `final` class

* Toegevoegd `ReplaceTimeRange()` methode

  Uitbreidingen `TimeRange` om een `replacementDuration` eigenschap. Voor de zaken MARK en DELETE, `replacementDuration` is 0.

* `TimeRangeCollection`

   * Toegevoegd `toReplaceMetadata()` hulpprogrammafunctie om te extraheren `timeRanges`.

   * Gewijzigd om te werken met `DELETE` en `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * Toegevoegd `createCustomTimeRangesFrom()` - Hiermee maakt u metagegevens voor gebruik van MARK/DELETE/REPLACE vanuit het JSON-bestand.
   * Verwijderd `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * Toegevoegd `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * Toegevoegd `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (niet gewijzigd)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * Toegevoegd `CustomRangesOpportunityGenerator` voor wanneer de metagegevens aangepaste bereiken bevatten

   * `doRetrieveResolvers()`

      * Toevoegen `CustomRangeResolver` for wanneer DELETE en REPLACE aangepaste bereiken aanwezig zijn in de metagegevens
      * Verplaatst `CustomAdMarkerResolver` voor `AuditudeResolver`

* Toegevoegd `CustomRangeOpportunityGenerator`

   * `doUpdate()` Laat leeg - geen update, VOD
   * `doProcess()` Hiermee maakt u een nieuwe plaatsing van een nieuw type `Placement.Delete_Range`

   * Toegevoegd `CustomRangeOppotunityGenerator` boven aan de lijst met generatoren in `DefaultContentFactory`verwijdert u bereiken dus vóór invoegingen.

   * Toegevoegd `createCustomRangeOpportunities` alle mogelijkheden creëren

     MARK - één mogelijkheid voor elk geldig merkbereik van `PlacementType.CUSTOM_RANGE` en `PlacementMode.MARK`

     DELETE - Eén mogelijkheid voor elk geldig verwijderingsbereik van `PlacementType.CUSTOM_RANGE` en `PlacementMode.DELETE`

     VERVANGEN - Twee mogelijkheden voor elke geldige vervang waaier:

      1. Een verwijderbereikmogelijkheid van `PlacementType.CUSTOM_RANGE` en `PlacementMode.DELETE`.

      1. Een primetime en een beslissing en kans van `PlacementType.MID_ROLL` of `PlacementType.PRE_ROLL` en `PlacementMode.FREEREPLACE`

* Toegevoegd `CustomRangeResolver`:

   * `doCanResolve()` retourneert `true` voor verwijderbereiken.

   * Toegevoegd `createDeleteRangeOperation()` om `DeleteRange` voor de plaatsing

* Toegevoegd `CustomRangeHelper`:

   * Algemene hulpprogrammaklasse voor het extraheren van Mark/Delete/Replace `timeRanges` en verwerken.
   * Toegevoegd `extractCustomRangesMetadata()`
   * Toegevoegd `extractCustomRanges()`
   * Toegevoegd `mergeRanges()` - Conflicten en subsets/samenvoegen oplossen

* `MediaPlayerTimeline`:

   * &quot;>In `executeOperation()`, als de bewerking `DeleteRange`, toegevoegde vraag om methode in verrichting te verwijderen

   * In `executeOperation()`, als de bewerking `NOPTimelineOperation` (leeg `AdBreaks` terugkomen van server), toegevoegde vraag om te ontruimen.

   * Toegevoegd `onDeleteRangeComplete()`
   * Toegevoegd `removeRange()`
   * In `adjustPlacement()`, for `PlacementMode.FREEREPLACE` -modus. De duur wordt op nul gezet. Deze tijdsduur is eerder vereist wanneer u een aanvraag indient `AdBreaks`Op dit punt moet de waarde nul zijn om alleen in te voegen.

* `VideoEngineTimeline` Toegevoegd `removeC3Ad()` - call `removeByLocalTime()` voor verwijderbereiken

* `AdSignalingModeGenerator`

   * `doConfigure()` - Niet oplossen als er geen mogelijkheid wordt gegenereerd
   * `createInitialOpportunity()` - Maak geen eerste kans voor `AdSignalingMode.CUSTOM_RANGE`. De `CustomRangeOpportunityGenerator` heeft betrekking op dit reeds.

* `DeleteRange`

   * Uitbreidingen `TimelineOperation`.
   * Gemaakt door `CustomRangeResolver` voor verwijdering en vervanging (schrapping deel van vervanging)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - verpakken toestaan
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` De `accepts()` de methode is gewijzigd om het verpakken van een ander plaatsingstype (vóór de rol, halverwege de rol, na de rol) mogelijk te maken;

* `AuditudeRequestHelper` Bugfixes om serveroverschrijving van Advertentieparameters toe te staan

* `AuditudeResolver` De `canBePacked()` methode gewijzigd om verpakking mogelijk te maken

* `CustomAdResolver` De `timeRange` extractiefuncties zijn verwijderd. We krijgen één plaatsing per keer en veranderen dat in een `AdBreakPlacement timelineOperation`.
