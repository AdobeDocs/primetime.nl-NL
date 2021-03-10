---
description: TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.
title: API-elementen voor doorbraak
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# API-elementen voor uitchecken{#blackout-api-elements}

TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.

U kunt het volgende gebruiken wanneer het uitvoeren van een stroomoplossing in uw speler.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Hiermee slaat u de momenteel geladen bron op als de achtergrondbron. Als `replaceCurrentResource` na deze methode wordt geroepen, blijft TVSDK manifest van het achtergrondpunt downloaden tot u `unregisterCurrentBackgroundItem` roept.

   * `unregisterCurrentBackgroundItem`  Wist de momenteel ingestelde achtergrondbron en stopt het ophalen en parseren van het achtergrondmanifest.

* **Het type** BlackoutMetadataA-metagegevens dat specifiek is voor black-outs.

   Dit staat u toe om nonseekable waaiers (een extra `TimeRange` attribuut genoemd `nonseekableRange`) op TVSDK te plaatsen. TvSDK controleert deze waaiers (of de gewenste vraagpositie binnen `nonseekableRange`) telkens als de gebruiker zoekt. Als deze is ingesteld en de gebruiker een bereik zoekt dat niet kan worden doorzocht, dwingt TVSDK de viewer tot de eindtijd van `seekableRange`.

* **START HIER** **** NEXTDefaultMetadataKeysEnable of maak preroll op een levende stroom onbruikbaar door  `ENABLE_LIVE_PREROLL` aan waar of vals te plaatsen. Indien onwaar, maakt TVSDK geen expliciete vraag van de advertentieserver naar pre-rol advertenties vóór de inhoudsplayback en zo speelt niet pre-rol. Dit heeft geen invloed op de middenrollen. De standaardwaarde is true.

* **TimedMetadataEvent**

   * `TIMED_METADATA_IN_BACKGROUND_AVAILABLE` subtype gebeurtenis - Wordt verzonden wanneer TVSDK een geabonneerde tag in het achtergrondmanifest detecteert.

* **Meldingen**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Type: Waarschuwing
      * Fout in downloaden achtergrondmanifest.
   * `SeekEvent.SEEK_POSITION_ADJUSTED` Wordt verzonden wanneer een zoekactie wordt uitgevoerd in een bereik dat niet kan worden gezocht.


