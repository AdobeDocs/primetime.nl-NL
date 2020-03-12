---
description: Deze wijzigingen in de Android TVSDK API ondersteunen en verwijderen en vervangen.
seo-description: Deze wijzigingen in de Android TVSDK API ondersteunen en verwijderen en vervangen.
seo-title: Wijzigingen in API voor verwijderen en vervangen toevoegen
title: Wijzigingen in API voor verwijderen en vervangen toevoegen
uuid: 2bb8a331-6851-4442-99de-b01500a0e1e2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Wijzigingen in API voor verwijderen en vervangen toevoegen{#ad-deletion-and-replacement-api-changes}

Deze wijzigingen in de Android TVSDK API ondersteunen en verwijderen en vervangen.

* `AdSignalingMode` Nieuwe aangepaste tijdbereik en signaalmodus

* `AdvertisingMetadata` Nieuw `setTimeRanges(TimeRangeCollection timeRanges, Metadata options)`: Hiermee stelt u de tijdbereiken in die u wilt markeren, verwijderen of vervangen bij het verwerken van metagegevens

* `ContentResolver`

   * Nieuw `public final boolean canResolve(PlacementOpportunity placementOpportunity)`
   * Nieuw `protected abstract boolean doCanResolve(PlacementOpportunity placementOpportunity)`

* Nieuwe `ContentRemoval` klasse

   `TimelineOperation` klasse die het tijdbereik definieert dat uit de tijdlijn moet worden verwijderd

* `AuditudeResolver`

   * Nieuw `private LinkedList<AuditudeRequest> _requestQueue`
   * Nieuw `void startConsumer()`: Begint verwerkend de Primetime en de rij van het beslissingsverzoek en zorgt ervoor dat elk verzoek met `MIN_INIT_REQUEST_INTERVAL` intervallen wordt uitgegeven

   * Nieuw `processReplacementRange()`: Extraheert tijdbereiken uit de metagegevens van de advertentie en genereert `PlacementInformations`en maakt een aanvraag voor primetime en besluitvorming die de metagegevens bevat `PlacementInformations`.

   * Nieuw `canDoResolver()`: Controleert of de plaatsingsmogelijkheid metagegevens voor primetime en besluitvorming bevat

* Nieuwe `CustomRangeHelper` klasse Helper die metagegevens over het tijdbereik extraheert uit metagegevens en subsets/overlap/ongeldige tijdbereiken verwijdert.

* Nieuwe oplosser voor `DeleteContentResolver` inhoud die de plaatsingsmogelijkheden van `PlacementInformation.Mode.DELETE`

* Nieuwe `NopTimelineOperation` tijdlijnbewerking wanneer geen plaatsing of vervanging van een advertentie-einde moet worden uitgevoerd. Deze klasse wordt gebruikt om tussen dit en te onderscheiden wanneer een fout tijdens het het oplossen van proces voorkomt.

* `TimelineOperationQueue` Controleert of de tijdlijnbewerking een bewerking is `NopTimelineOperation` voordat deze wordt verwerkt.

* `CustomAdMarkersContentResolver` Nieuw `canDoResolve()`: Controleert of een plaatsingsmogelijkheid van het type is `Mode.MARK`

* `MetadataResolver` Nieuw `canDoResolve()`: Controleert of een plaatsingsmogelijkheid van het type is `Mode.INSERT`

* `DefaultMetadataKeys` Nieuw `TIME_RANGES_METADATA_KEY("time_ranges_metadata_key")`

* `PlacementInformation`

   * Nieuwe modus `enum (INSERT, DELETE, REPLACE, MARK)`
   * Nieuw type `CUSTOM_TIME_RANGES`

* `TimeRange` Nieuw `compareTo(TimeRange timeRange)`: Zo kan TimeRanges sorteren op basis van begintijd

* Met Nieuw `ReplacementTimeRange` breidt u de `TimeRange` klasse uit die een vervangingsreeks, met een parameter `begin`, `end`en `replacement-duration` vertegenwoordigt.

* `TimeRangeCollection`

   * Nieuw `MARK_RANGES, DELETE_RANGES, REPLACE_RANGES`
   * Naam gewijzigd `CUSTOM_AD_MARKERS` in `MARK_RANGES`

   * Gewijzigd `toMetadata(Metadata options)` om bereik voor verwijderen/markeren/vervangen in metagegevens voor advertenties te plaatsen.

* `MediaPlayerNotification`

   * Nieuw `UNDEFINED_TIME_RANGES`: Wanneer de advertentie-signalerende wijze de Kaart van de Server of Duidelijke Gebruik is, en reeksen vervangt ook in de ademetagegevens zijn, vervangt waaiers worden genegeerd.
   * Nieuw `REPLACE_RANGES_NOT_AVAILABLE`: Wanneer de ad signalerende wijze de Waaier van de Tijd van de Douane is en reeksen vervangt niet beschikbaar, zal een waarschuwing worden verzonden.

* `AdvertisingFactory` Nieuw `public abstract List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultAdvertisingFactory` Nieuw `public List<ContentResolver> createContentResolvers(MediaPlayerItem item)`

* `DefaultContentResolverFactory` Nieuw `public static List<ContentResolver> createContentResolvers(MediaResource resource, Context context)`

* `DefaultMediaPlayer`

   * In `prepareToPlay()`: Hiermee maakt u een eerste zoekopdracht tot 0, omdat bij het verwijderen van het bereik de mediaspeler niet automatisch wordt afgespeeld. `[0,n]`

   * In `prepareToPlay()`: Hiermee doorloopt u de lijst met initiële plaatsingsgegevens die moeten worden opgelost. `mediaplayerclient`

   * In `extractAdSignalingMode()`: Ga naar de nieuwe modus Aangepast tijdbereik.
   * Nieuw `private static List<PlacementInformation> createInitalPlacementInformations()`: Hiermee genereert u de initiële plaatsingsinformatie voor de ad-signaalmodus en de inhoudsoplossers (afgeleid van metagegevens van advertenties).
   * In `ContentPlacementCompletedListener`: Controleert om te zien of `mediaPlayerClient` is `doneInitialResolving` alvorens `endAdResolving`.

* `MediaPlayerClient`

   * Nieuw `List<ContentResolver> _contentResolvers`
   * Nieuw `int _reservations`
   * Nieuw `lookupContentResolver(PlacementOpportunity placementOpportunity)`: Zoekt op welke oplosser het bestand kan oplossen `PlacementOpportunity`.

   * Gewijzigde code voor het maken van meerdere inhoudsoplossers.
   * Nieuw `public boolean doneInitialResolving()`: Controleert of er nog mogelijkheden zijn om op te lossen.

* `VideoEngineTimeline`

   * Nieuw `removeContent(TimelineOperation timelineOperation)`: Hiermee wordt een bepaald inhoudsbereik uit de tijdlijn verwijderd.
   * Nieuw `removeContentByLocalTime(long begin, long end)`: Hiermee verwijdert u inhoud op lokale tijd die u hebt gegeven `begin` en `end`.

* `DefaultOpportunityDetectorFactory` Gewijzigd `createOpportunityDetector`: Voor stromen VOD, terugkeer slechts een nieuwe `SpliceOutOpportunityDetector` als er geen SEMARKER of de waaiers van de VERVANG zijn (aangezien die waaiers prioriteit over de signalerende wijze hebben).

