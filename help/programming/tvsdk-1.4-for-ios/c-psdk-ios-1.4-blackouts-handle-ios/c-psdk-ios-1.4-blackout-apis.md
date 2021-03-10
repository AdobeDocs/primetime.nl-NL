---
description: TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.
title: API-elementen voor doorbraak
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# API-elementen voor uitchecken{#blackout-api-elements}

TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.

U kunt het volgende gebruiken wanneer het uitvoeren van een stroomoplossing in uw speler.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Hiermee slaat u de momenteel geladen bron op als de achtergrondbron. Als `replaceCurrentItemWithPlayerItem` na deze methode wordt geroepen, blijft TVSDK manifest van het achtergrondpunt tot u `unregisterCurrentBackgroundItem`, `stop`, of `reset` roept.

   * `unregisterCurrentBackgroundItem` Stelt het achtergronditem in op nul en stopt het ophalen en parseren van het achtergrondmanifest.

* **PTMetadata.** PTBlackoutMetadataA- `PTMetadata` klasse die specifiek is voor black-outs.

   Hierdoor kunt u niet-doorzoekbare bereiken (een array van `CMTimeRanges`) instellen op TVSDK. TVSDK controleert deze waaiers telkens als de gebruiker zoekt. Als deze is ingesteld en de gebruiker een bereik zoekt dat niet kan worden doorzocht, dwingt TVSDK de viewer tot het einde van het bereik dat niet kan worden doorzocht.

* **START HIER** **** NEXTPTAdMetadataEnable of disable pre-roll op een levende stroom door  `enableLivePreroll` aan JA of GEEN te plaatsen. Indien NO, maakt TVSDK geen expliciete vraag van de advertentieserver naar pre-rol advertenties vóór de inhoudsplayback en speelt zo niet pre-rol. Dit heeft geen invloed op de middenrollen. De standaardwaarde is JA.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Gepost wanneer TVSDK een geabonneerde tag in het achtergrondmanifest detecteert en er een nieuwe  `PTTimedMetadata` instantie van wordt gemaakt. Het voorwerp van het bericht is de `PTMediaPlayerItem` instantie die momenteel speelt. U kunt de `PTTimedMetadata` instantie van het `userInfo` woordenboek van het bericht halen gebruikend `PTTimedMetadataKey` sleutel.

   * `PTBackgroundManifestErrorNotification` - Wordt verzonden wanneer de mediaspeler het achtergrondmanifest volledig niet laadt, dat wil zeggen dat alle stream-URL&#39;s een fout of een ongeldige reactie retourneren. Het voorwerp van het bericht is de `PTMediaPlayerItem` instantie die momenteel speelt.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Type: Waarschuwing
      * Fout in downloaden achtergrondmanifest.
   * `INVALID_SEEK_WARNING` Wordt verzonden wanneer een zoekopdracht wordt uitgevoerd in een bereik dat niet kan worden doorzocht ( `nonSeekableRanges` ingesteld in  `PTBlackoutMetadata`).


