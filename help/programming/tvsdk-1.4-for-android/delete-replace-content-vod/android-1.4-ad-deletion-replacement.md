---
description: Deze wijzigingen in de Android TVSDK API ondersteunen en verwijderen en vervangen.
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Wijzigingen in API voor verwijderen en vervangen toevoegen{#ad-deletion-and-replacement-api-changes}

Deze wijzigingen in de Android TVSDK API ondersteunen en verwijderen en vervangen.

* `AdSignalingMode` Nieuwe aangepaste tijdbereik en signaalmodus

* `AdvertisingMetadata` Nieuw  `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: Hiermee stelt u de tijdbereiken in die u wilt markeren, verwijderen of vervangen bij het verwerken van metagegevens

* `ContentResolver`

   * Nieuwe `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Nieuwe `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Nieuwe `ContentRemoval`-klasse

   `TimelineOperation` klasse die het tijdbereik definieert dat uit de tijdlijn moet worden verwijderd

* `AuditudeResolver`

   * Nieuwe `private LinkedList<AuditudeRequest> _requestQueue`
   * Nieuwe `void startConsumer()`: Begint verwerkend de Primetime en de rij van het beslissingsverzoek en zorgt ervoor dat elk verzoek bij `MIN_INIT_REQUEST_INTERVAL` intervallen wordt uitgegeven

   * Nieuwe `processReplacementRange()`: Extraheert tijdbereiken uit de metagegevens van de advertentie en genereert `PlacementInformations`, en maakt een aanvraag voor primetime en besluitvorming die `PlacementInformations` bevat.

   * Nieuwe `canDoResolver()`: Controleert of de plaatsingsmogelijkheid metagegevens voor primetime en besluitvorming bevat

* Nieuwe klasse `CustomRangeHelper` Helper die metagegevens uit het tijdbereik extraheert uit metagegevens en subsets/overlap/ongeldige tijdbereiken verwijdert.

* Nieuwe `DeleteContentResolver`-inhoudoplosser die plaatsingsmogelijkheden van `PlacementInformation.Mode.DELETE` verhelpt

* Nieuwe `NopTimelineOperation` Nieuwe tijdlijnbewerking wanneer geen plaatsing of vervanging van een advertentie-einde moet worden uitgevoerd. Deze klasse wordt gebruikt om tussen dit en te onderscheiden wanneer een fout tijdens het het oplossen van proces voorkomt.

* `TimelineOperationQueue` Controleert of de tijdlijnbewerking een bewerking is  `NopTimelineOperation` voordat deze wordt verwerkt.

* `CustomAdMarkersContentResolver` Nieuw  `canDoResolve()`: Controleert of een plaatsingsmogelijkheid van het type is  `Mode.MARK`

* `MetadataResolver` Nieuw  `canDoResolve()`: Controleert of een plaatsingsmogelijkheid van het type is  `Mode.INSERT`

* `DefaultMetadataKeys` Nieuw  `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Nieuwe modus `enum (INSERT, DELETE, REPLACE, MARK)`
   * Nieuw type `CUSTOM_TIME_RANGES`

* `TimeRange` Nieuw  `compareTo(TimeRange timeRange)`: Zo kan TimeRanges sorteren op basis van begintijd

* Nieuwe `ReplacementTimeRange` breidt de `TimeRange` klasse uit die een vervangingstimerange, met een `begin`, `end`, en `replacement-duration` parameter vertegenwoordigt.

* `TimeRangeCollection`

   * Nieuwe `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Naam gewijzigd in `CUSTOM_AD_MARKERS` in `MARK_RANGES`

   * Gewijzigd `toMetadata(Metadata options)` om reeksen voor verwijderen/markeren/vervangen in metagegevens voor advertenties te plaatsen.

* `MediaPlayerNotification`

   * Nieuwe `UNDEFINED_TIME_RANGES`: Wanneer de advertentie-signalerende wijze de Kaart van de Server of Duidelijke Gebruik is, en reeksen vervangt ook in de ademetagegevens zijn, vervangt waaiers worden genegeerd.
   * Nieuwe `REPLACE_RANGES_NOT_AVAILABLE`: Wanneer de ad signalerende wijze de Waaier van de Tijd van de Douane is en reeksen vervangt niet beschikbaar, zal een waarschuwing worden verzonden.

* `AdvertisingFactory` Nieuw  `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Nieuw  `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Nieuw  `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * In `prepareToPlay()`: Hiermee maakt u een eerste zoekopdracht tot 0, omdat bij het verwijderen van het bereik `[0,n]` de mediaspeler niet automatisch wordt afgespeeld.

   * In `prepareToPlay()`: Hiermee doorloopt u de lijst met initiële plaatsingsgegevens die `mediaplayerclient` moet oplossen.

   * In `extractAdSignalingMode()`: Ga naar de nieuwe modus Aangepast tijdbereik.
   * Nieuwe `private static List<PlacementInformation> createInitalPlacementInformations()`: Hiermee genereert u de initiële plaatsingsinformatie voor de ad-signaalmodus en de inhoudsoplossers (afgeleid van metagegevens van advertenties).
   * In `ContentPlacementCompletedListener`: Controleert of `mediaPlayerClient` `doneInitialResolving` is voordat `endAdResolving` wordt aangeroepen.

* `MediaPlayerClient`

   * Nieuwe `List<ContentResolver> _contentResolvers`
   * Nieuwe `int _reservations`
   * Nieuwe `lookupContentResolver(PlacementOpportunity placementOpportunity)`: Zoekt op welke oplosser `PlacementOpportunity` kan oplossen.

   * Gewijzigde code voor het maken van meerdere inhoudsoplossers.
   * Nieuwe `public boolean doneInitialResolving()`: Controleert of er nog mogelijkheden zijn om op te lossen.

* `VideoEngineTimeline`

   * Nieuwe `removeContent(TimelineOperation timelineOperation)`: Hiermee wordt een bepaald inhoudsbereik uit de tijdlijn verwijderd.
   * Nieuwe `removeContentByLocalTime(long begin, long end)`: Verwijdert inhoud volgens lokale tijd gegeven `begin` en `end`.

* `DefaultOpportunityDetectorFactory` Gewijzigd  `createOpportunityDetector`: Voor stromen VOD, keert slechts een nieuwe terug  `SpliceOutOpportunityDetector` als er geen SEMARKER of de waaiers van de VERVANG zijn (aangezien die waaiers prioriteit over de signalerende wijze hebben).

