---
description: Deze wijzigingen in de Android TVSDK API ondersteunen en verwijderen en vervangen.
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Wijzigingen in API voor verwijderen en vervangen toevoegen{#ad-deletion-and-replacement-api-changes}

Deze wijzigingen in de Android TVSDK API ondersteunen en verwijderen en vervangen.

* `AdSignalingMode` Nieuwe aangepaste tijdbereik en signaalmodus

* `AdvertisingMetadata` Nieuw `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: Hiermee stelt u de tijdbereiken in die u wilt markeren, verwijderen of vervangen bij het verwerken van metagegevens

* `ContentResolver`

   * Nieuw `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Nieuw `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Nieuw `ContentRemoval` class

  `TimelineOperation` klasse die het tijdbereik definieert dat uit de tijdlijn moet worden verwijderd

* `AuditudeResolver`

   * Nieuw `private LinkedList<AuditudeRequest> _requestQueue`
   * Nieuw `void startConsumer()`: Begint verwerkend de Primetime en de rij van het beslissingsverzoek en zorgt ervoor dat elk verzoek bij wordt uitgegeven `MIN_INIT_REQUEST_INTERVAL` intervallen

   * Nieuw `processReplacementRange()`: Extraheert tijdbereiken uit de metagegevens van de advertentie en genereert deze `PlacementInformations`en maakt een aanvraag voor Primetime en besluitvorming met de `PlacementInformations`.

   * Nieuw `canDoResolver()`: Controleert of de plaatsingsmogelijkheid metagegevens voor primetime en besluitvorming bevat

* Nieuw `CustomRangeHelper` De klasse van de hulp die meta-gegevens van de tijdwaaier uit advertentiemetagegevens haalt, en subsets/overlappingen/ongeldige tijdwaaiers verwijdert.

* Nieuw `DeleteContentResolver` Inhoud oplossen die plaatsingskansen van `PlacementInformation.Mode.DELETE`

* Nieuw `NopTimelineOperation` Nieuwe tijdlijnbewerking die aangeeft wanneer geen plaatsing of vervanging van een advertentie-einde moet worden uitgevoerd. Deze klasse wordt gebruikt om tussen dit en te onderscheiden wanneer een fout tijdens het het oplossen van proces voorkomt.

* `TimelineOperationQueue` Controleert of de tijdlijnbewerking een `NopTimelineOperation` vóór verwerking.

* `CustomAdMarkersContentResolver` Nieuw `canDoResolve()`: Controleert of een plaatsingsmogelijkheid van het type is `Mode.MARK`

* `MetadataResolver` Nieuw `canDoResolve()`: Controleert of een plaatsingsmogelijkheid van het type is `Mode.INSERT`

* `DefaultMetadataKeys` Nieuw `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Nieuwe modus `enum (INSERT, DELETE, REPLACE, MARK)`
   * Nieuw type `CUSTOM_TIME_RANGES`

* `TimeRange` Nieuw `compareTo(TimeRange timeRange)`: Zo kan TimeRanges sorteren op basis van begintijd

* Nieuw `ReplacementTimeRange` Hiermee breidt u de `TimeRange` klasse die een vervangingsreeks vertegenwoordigt, met een `begin`, `end`, en `replacement-duration` parameter.

* `TimeRangeCollection`

   * Nieuw `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Naam gewijzigd `CUSTOM_AD_MARKERS` tot `MARK_RANGES`

   * gewijzigd `toMetadata(Metadata options)` om reeksen voor verwijderen/markeren/vervangen in metagegevens voor advertenties te plaatsen.

* `MediaPlayerNotification`

   * Nieuw `UNDEFINED_TIME_RANGES`: Wanneer de ad-signaalmodus Server Map of Manifest Cues is en waaiers vervangen zich ook in de metagegevens van de advertentie bevinden, worden reeksen vervangen genegeerd.
   * Nieuw `REPLACE_RANGES_NOT_AVAILABLE`: Wanneer de ad-signaalmodus Aangepaste tijdbereiken is en reeksen vervangen niet beschikbaar is, wordt een waarschuwing verzonden.

* `AdvertisingFactory` Nieuw `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Nieuw `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Nieuw `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * In `prepareToPlay()`: Hiermee wordt een eerste zoekopdracht ingesteld op 0, omdat het bereik indien `[0,n]` wordt verwijderd, wordt de mediaspeler niet automatisch afgespeeld.

   * In `prepareToPlay()`: Wordt door de lijst met initiële plaatsingsgegevens voor `mediaplayerclient` om op te lossen.

   * In `extractAdSignalingMode()`: Kies deze optie voor de nieuwe modus Aangepast tijdbereik.
   * Nieuw `private static List<PlacementInformation> createInitalPlacementInformations()`: Hiermee genereert u de initiële plaatsingsinformatie voor de ad-signaalmodus en de inhoudsoplossers (afgeleid van metagegevens van advertenties).
   * In `ContentPlacementCompletedListener`: Controleert of `mediaPlayerClient` is `doneInitialResolving` voordat wordt aangeroepen `endAdResolving`.

* `MediaPlayerClient`

   * Nieuw `List<ContentResolver> _contentResolvers`
   * Nieuw `int _reservations`
   * Nieuw `lookupContentResolver(PlacementOpportunity placementOpportunity)`: hiermee wordt gezocht naar de oplosser die het `PlacementOpportunity`.

   * Gewijzigde code voor het maken van meerdere inhoudsoplossers.
   * Nieuw `public boolean doneInitialResolving()`: Controleert of er nog mogelijkheden zijn om op te lossen.

* `VideoEngineTimeline`

   * Nieuw `removeContent(TimelineOperation timelineOperation)`: Hiermee wordt een bepaald inhoudsbereik uit de tijdlijn verwijderd.
   * Nieuw `removeContentByLocalTime(long begin, long end)`: Hiermee wordt inhoud verwijderd volgens lokale tijd die wordt gegeven `begin` en `end`.

* `DefaultOpportunityDetectorFactory` gewijzigd `createOpportunityDetector`: Retourneer voor VOD-streams alleen een nieuwe `SpliceOutOpportunityDetector` als er geen Banden van het KERK of van de VERVANGING zijn (aangezien die waaiers prioriteit over de signalerende wijze hebben).
