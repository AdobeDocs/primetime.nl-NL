---
description: TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.
title: API-elementen voor doorbraak
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# API-elementen voor doorbraak{#blackout-api-elements}

TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.

U kunt het volgende gebruiken wanneer het uitvoeren van een stroomoplossing in uw speler.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Hiermee slaat u de momenteel geladen bron op als de achtergrondbron. Indien `replaceCurrentResource` wordt geroepen na deze methode, blijft TVSDK manifest van het achtergrondpunt downloaden tot u roept `unregisterCurrentBackgroundItem`.

   * `unregisterCurrentBackgroundItem`  Wist de momenteel ingestelde achtergrondbron en stopt het ophalen en parseren van het achtergrondmanifest.

* **BlackoutMetadata** Een type metagegevens dat specifiek is voor stroomuitval.

  Hierdoor kunt u niet-doorzoekbare bereiken instellen (een extra `TimeRange` attribuut called `nonseekableRange`) op TVSDK. TVSDK controleert deze bereiken (of de gewenste zoekpositie binnen een bereik valt `nonseekableRange`) iedere keer dat de gebruiker zoekt. Als deze is ingesteld en de gebruiker een bereik zoekt dat niet doorzoekbaar is, dwingt TVSDK de viewer tot het einde van de `seekableRange`.

* **HIER VOLGENDE BEGINNEN** **DefaultMetadataKeys** Voorvertoning op een live stream in- of uitschakelen door het instellen `ENABLE_LIVE_PREROLL` naar waar of onwaar. Indien onwaar, maakt TVSDK geen expliciete vraag van de advertentieserver naar pre-rol advertenties vóór de inhoudsplayback en zo speelt niet pre-rol. Dit heeft geen invloed op de halverwege de rol. De standaardwaarde is true.

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` subtype gebeurtenis - Wordt verzonden wanneer TVSDK een geabonneerde tag in het achtergrondmanifest detecteert.

* **Meldingen**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Type: waarschuwing
      * Fout in downloaden achtergrondmanifest.

   * `SeekEvent.SEEK_POSITION_ADJUSTED` Wordt verzonden wanneer een zoekactie wordt uitgevoerd in een bereik dat niet kan worden gezocht.
