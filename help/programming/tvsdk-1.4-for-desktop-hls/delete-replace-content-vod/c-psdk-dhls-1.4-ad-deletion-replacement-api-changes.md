---
description: Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.
seo-description: Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.
seo-title: Wijzigingen in API voor verwijderen en vervangen toevoegen
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
uuid: 9d208d3b-6459-4aaf-bc56-53c405ccc1b6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Wijzigingen in API voor verwijderen en vervangen toevoegen {#ad-deletion-and-replacement-api-changes}

Deze wijzigingen in TVSDK ondersteunen het verwijderen en vervangen van bestanden.

* `AdSignalingMode` Toegevoegde  `CUSTOM_RANGES` signaalmodus.

* `OpportunityGenerator`  `extractAdSignalingMode()` - Stel in  `AdSignalingMode.CUSTOM_RANGES` of u vervangingsbereiken wilt invoegen in de metagegevens.

* `PlacementType` Toegevoegd  `CUSTOM_RANGE` type.

* `PlacementMode`

   * Modus `DELETE` toegevoegd.
   * Modus `MARK` toegevoegd
   * Modus `FreeReplace` toegevoegd - Deze modus heeft een duur maar is een zuivere invoeging

* `TimeRange` Niet langer een  `final` klasse

* Toegevoegde methode `ReplaceTimeRange()`

   Breidt `TimeRange` uit om een `replacementDuration` bezit te hebben. Voor de gevallen MARK en DELETE is `replacementDuration` 0.

* `TimeRangeCollection`

   * `toReplaceMetadata()` hulpprogrammafunctie toegevoegd om `timeRanges` te extraheren.

   * Gewijzigd om te werken met `DELETE` en `REPLACE`

   * `METADATA_KEY_CUSTOM_MARK_RANGES`,  `METADATA_KEY_CUSTOM_DELETE_RANGES`,  `METADATA_KEY_CUSTOM_REPLACE_RANGES`

* `CatalogItem`

   * Toegevoegd `createCustomTimeRangesFrom()` - Creeert meta-gegevens voor MARK/DELETE/REPLACE gebruiksgevallen van het JSON dossier.
   * Verwijderd `createCustomAdMarkersMetadataFrom()`

* `DefaultMetadataKeys`

   * `CUSTOM_DELETE_RANGES_METADATA_KEY` toegevoegd
   * `CUSTOM_REPLACE_RANGES_METADATA_KEY` toegevoegd
   * `CUSTOM_AD_MARKERS_METADATA_KEY` (niet gewijzigd)

* `DefaultContentFactory`

   * `doRetrieveGenerators()`

      * `CustomRangesOpportunityGenerator` toegevoegd als de metagegevens aangepaste bereiken bevatten
   * `doRetrieveResolvers()`

      * Voeg `CustomRangeResolver` toe voor wanneer de DELETE en VERVANGEN douanewaaiers in de meta-gegevens aanwezig zijn
      * `CustomAdMarkerResolver` voor `AuditudeResolver` verplaatst


* `CustomRangeOpportunityGenerator` toegevoegd

   * `doUpdate()` Laat leeg - geen update, VOD
   * `doProcess()` Hiermee maakt u een nieuwe plaatsing van een nieuw type  `Placement.Delete_Range`

   * `CustomRangeOppotunityGenerator` toegevoegd aan de bovenkant van de lijst van generatoren in `DefaultContentFactory`, zodat worden schrappingswaaiers verwerkt vóór toevoegingen.

   * `createCustomRangeOpportunities` toegevoegd om alle mogelijkheden te creëren

      MARK - één mogelijkheid voor elk geldig markeringsbereik van `PlacementType.CUSTOM_RANGE` en `PlacementMode.MARK`

      DELETE - Eén mogelijkheid voor elk geldig verwijderbereik van `PlacementType.CUSTOM_RANGE` en `PlacementMode.DELETE`

      VERVANGEN - Twee mogelijkheden voor elke geldige vervang waaier:

      1. Een verwijderingsbereikmogelijkheid van `PlacementType.CUSTOM_RANGE` en `PlacementMode.DELETE`.

      1. Een primetime- en beslissings- en opportuniteit van `PlacementType.MID_ROLL` of `PlacementType.PRE_ROLL` en `PlacementMode.FREEREPLACE`

* Toegevoegd `CustomRangeResolver`:

   * `doCanResolve()` retourneert  `true` voor verwijderbereiken.

   * `createDeleteRangeOperation()` toegevoegd om `DeleteRange` voor de plaatsing te creëren

* Toegevoegd `CustomRangeHelper`:

   * Gemeenschappelijke hulpprogrammaklasse om Mark/Delete/Replace `timeRanges` te halen en hen te verwerken.
   * `extractCustomRangesMetadata()` toegevoegd
   * `extractCustomRanges()` toegevoegd
   * `mergeRanges()` toegevoegd - Hiermee worden conflicten en subsets/samengevoegde

* `MediaPlayerTimeline`:

   * &quot;>Als de bewerking `executeOperation()` is, voegt u in &lt;a0/> een aanroep toe om de methode in de bewerking te verwijderen.`DeleteRange`

   * Als in `executeOperation()` de bewerking `NOPTimelineOperation` is (lege `AdBreaks` die terugkomt van de server), voegt u een aanroep toe om te wissen.

   * `onDeleteRangeComplete()` toegevoegd
   * `removeRange()` toegevoegd
   * In `adjustPlacement()`, voor `PlacementMode.FREEREPLACE` wijze, centreerde uit de duur. Deze duur is eerder nodig wanneer `AdBreaks` wordt aangevraagd, op dit punt moet deze nul zijn om zuiver invoeging te zijn.

* `VideoEngineTimeline` Toegevoegd  `removeC3Ad()` - vraag  `removeByLocalTime()` voor schrappingswaaiers

* `AdSignalingModeGenerator`

   * `doConfigure()` - Niet oplossen als er geen mogelijkheid wordt gegenereerd
   * `createInitialOpportunity()` - Maak geen eerste kans voor  `AdSignalingMode.CUSTOM_RANGE`. De `CustomRangeOpportunityGenerator` behandelt dit al.

* `DeleteRange`

   * Breidt `TimelineOperation` uit.
   * Gemaakt door `CustomRangeResolver` voor verwijderen en vervangen (het verwijderingsgedeelte van vervanging)

* `AuditudeConstant`

   * `MAX_PLACEMENTS_PER_REQUEST 1->5` - verpakken toestaan
   * `MINIMUM_AD_DURATION 10->5`

* `AuditudeRequest` De  `accepts()` methode werd gewijzigd om het verpakken van verschillende plaatsingstypen mogelijk te maken (vóór de rol, halverwege de rol, na de rol)

* `AuditudeRequestHelper` Bugfixes om serveroverschrijvingen van advertentieparameters toe te staan

* `AuditudeResolver` De  `canBePacked()` methode is gewijzigd om het verpakken mogelijk te maken

* `CustomAdResolver` De  `timeRange` extractiefuncties zijn verwijderd. We krijgen één plaatsing tegelijk, en veranderen dat in een `AdBreakPlacement timelineOperation`.

