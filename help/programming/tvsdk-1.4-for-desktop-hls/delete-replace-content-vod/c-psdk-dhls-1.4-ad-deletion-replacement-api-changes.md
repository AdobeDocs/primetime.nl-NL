---
description: Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.
seo-description: Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.
seo-title: Wijzigingen in API voor verwijderen en vervangen toevoegen
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Wijzigingen in API voor verwijderen en vervangen toevoegen {#ad-deletion-and-replacement-api-changes}

Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.

* `AdSignalingMode` Toegevoegde `CUSTOM_RANGES` signaalmodus.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Stel in `AdSignalingMode.CUSTOM_RANGES` of u reeksen wilt vervangen in de metagegevens.

* `PlacementType` Toegevoegd `CUSTOM_RANGE` type.

* `PlacementMode`

   * Toegevoegde `DELETE` modus.
   * Toegevoegde `MARK` modus
   * Toegevoegde `FreeReplace` modus - Deze modus heeft een duur maar is een zuivere invoeging

* `TimeRange` Niet langer een `final` klasse

* Toegevoegde `ReplaceTimeRange()` methode

   Hiermee wordt `TimeRange` de eigenschap uitgebreid met een `replacementDuration` eigenschap. Voor de gevallen MARK en DELETE `replacementDuration` is 0.

* `TimeRangeCollection`

   * Toegevoegde `toReplaceMetadata()` hulpprogrammafunctie om te extraheren `timeRanges`.

   * Gewijzigd om te werken met `DELETE` en `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`, `METADATA_KEY_CUSTOM_DELETE_RANGES`, `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * Toegevoegd `createCustomTimeRangesFrom()` - maakt metagegevens voor de gebruiksgevallen MARK/DELETE/REPLACE uit het JSON-bestand.
   * Verwijderd `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * Toegevoegd `CUSTOM_DELETE_RANGES_METADATA_KEY`
   * Toegevoegd `CUSTOM_REPLACE_RANGES_METADATA_KEY`
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (niet gewijzigd)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * Toegevoegd `CustomRangesOpportunityGenerator` voor wanneer de metagegevens aangepaste bereiken bevatten
   * `doRetrieveResolvers()`

      * Toevoegen `CustomRangeResolver` voor wanneer aangepaste bereiken DELETE en REPLACE aanwezig zijn in de metagegevens
      * Verplaatst `CustomAdMarkerResolver` voor `AuditudeResolver`


* Toegevoegd `CustomRangeOpportunityGenerator`

   * `doUpdate()` Laat leeg - geen update, VOD
   * `doProcess()` Hiermee maakt u een nieuwe plaatsing van een nieuw type `Placement.Delete_Range`

   * Toegevoegd `CustomRangeOppotunityGenerator` aan de bovenkant van de generatorlijst in `DefaultContentFactory`, zodat worden de schrappingswaaiers verwerkt vóór toevoegingen.

   * Toegevoegd `createCustomRangeOpportunities` om alle mogelijkheden te creëren

      MARK - één mogelijkheid voor elk geldig merkbereik van `PlacementType.CUSTOM_RANGE` en `PlacementMode.MARK`

      DELETE - Eén mogelijkheid voor elk geldig verwijderingsbereik van `PlacementType.CUSTOM_RANGE` en `PlacementMode.DELETE`

      VERVANGEN - Twee mogelijkheden voor elke geldige vervang waaier:

      1. Een verwijderbereik van `PlacementType.CUSTOM_RANGE` en `PlacementMode.DELETE`.

      1. Een primetime en een beslissing en mogelijkheid van `PlacementType.MID_ROLL` of `PlacementType.PRE_ROLL` en `PlacementMode.FREEREPLACE`

* Toegevoegd `CustomRangeResolver`:

   * `doCanResolve()` retourneert `true` voor verwijderbereiken.

   * Toegevoegd `createDeleteRangeOperation()` om `DeleteRange` voor de plaatsing te creëren

* Toegevoegd `CustomRangeHelper`:

   * Algemene hulpprogrammaklasse om Mark/Delete/Replace te extraheren `timeRanges` en te verwerken.
   * Toegevoegd `extractCustomRangesMetadata()`
   * Toegevoegd `extractCustomRanges()`
   * Toegevoegd `mergeRanges()` - Conflicten en subsets/samengevoegde bestanden oplossen

* `MediaPlayerTimeline`:

   * &quot;>In `executeOperation()`, als de bewerking is `DeleteRange`uitgevoerd, voegt u een aanroep toe om de methode in de bewerking te verwijderen

   * In `executeOperation()`, als de verrichting `NOPTimelineOperation` (leeg `AdBreaks` terugkomend van server) is, toegevoegde vraag om te ontruimen.

   * Toegevoegd `onDeleteRangeComplete()`
   * Toegevoegd `removeRange()`
   * In `adjustPlacement()`, voor `PlacementMode.FREEREPLACE` wijze, centreerde uit de duur. Deze tijdsduur is eerder nodig wanneer u daarom vraagt `AdBreaks`, op dit moment moet deze nul zijn om alleen in te voegen.

* `VideoEngineTimeline` Toegevoegd `removeC3Ad()` - vraag `removeByLocalTime()` voor schrappingswaaiers

* `AdSignalingModeGenerator`

   * `doConfigure()` - Niet oplossen als er geen mogelijkheid wordt gegenereerd
   * `createInitialOpportunity()` - Maak geen eerste kans voor `AdSignalingMode.CUSTOM_RANGE`. Dat `CustomRangeOpportunityGenerator` komt al aan de orde.

* `DeleteRange`

   * Breidt uit `TimelineOperation`.
   * Gemaakt door `CustomRangeResolver` voor verwijderen en vervangen (het verwijderingsgedeelte van vervanging)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - verpakken toestaan
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` De `accepts()` methode werd gewijzigd om het verpakken van verschillende plaatsingstypen mogelijk te maken (vóór de rol, halverwege de rol, na de rol)

* `AuditudeRequestHelper` Bugfixes om serveroverschrijving van Advertentieparameters toe te staan

* `AuditudeResolver` De `canBePacked()` methode is gewijzigd om verpakken mogelijk te maken

* `CustomAdResolver` De `timeRange` extractiefuncties zijn verwijderd. We krijgen één plaatsing per keer en veranderen dat in een `AdBreakPlacement timelineOperation`.

