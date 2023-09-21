---
description: TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.
title: API-elementen voor doorbraak
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# API-elementen voor doorbraak {#blackout-api-elements}

TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.

U kunt het volgende gebruiken wanneer het uitvoeren van een stroomoplossing in uw speler.

* **PTMediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Hiermee slaat u de momenteel geladen bron op als de achtergrondbron. Indien `replaceCurrentItemWithPlayerItem` wordt geroepen na deze methode, blijft TVSDK manifest van het achtergrondpunt downloaden tot u roept `unregisterCurrentBackgroundItem` , `stop`, of `reset` .

   * `unregisterCurrentBackgroundItem` Stelt het achtergronditem in op nul en stopt het ophalen en parseren van het achtergrondmanifest.

* **PTMetadata.PTBlackoutMetadata** A `PTMetadata` een specifieke klasse voor stroomuitval.

  Hierdoor kunt u niet-doorzoekbare bereiken instellen (een array van `CMTimeRanges`) op TVSDK. TVSDK controleert deze waaiers telkens als de gebruiker zoekt. Als deze is ingesteld en de gebruiker een bereik zoekt dat niet kan worden doorzocht, dwingt TVSDK de viewer tot het einde van het bereik dat niet kan worden doorzocht.

* **HIER VOLGENDE BEGINNEN** **PTAdMetadata** Pre-roll op een live stream in- of uitschakelen door `enableLivePreroll` naar JA of NEE. Indien NO, maakt TVSDK geen expliciete vraag van de advertentieserver naar pre-rol advertenties vóór de inhoudsplayback en speelt zo niet pre-rol. Dit heeft geen invloed op de halverwege de rol. De standaardwaarde is JA.

* **NSNotifications**

   * `PTTimedMetadataChangedInBackgroundNotification` - Gepost wanneer TVSDK een geabonneerde tag in het achtergrondmanifest en een nieuw `PTTimedMetadata` -instantie is er op voorbereid. Het doel van de melding is `PTMediaPlayerItem` -instantie die momenteel wordt afgespeeld. U kunt de `PTTimedMetadata` instantie van de kennisgeving `userInfo` woordenboek met de `PTTimedMetadataKey` toets.

   * `PTBackgroundManifestErrorNotification` - Wordt verzonden wanneer de mediaspeler het achtergrondmanifest volledig niet laadt, dat wil zeggen dat alle stream-URL&#39;s een fout of een ongeldige reactie retourneren. Het doel van de melding is `PTMediaPlayerItem` -instantie die momenteel wordt afgespeeld.

* **PTNotification**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Type: waarschuwing
      * Fout in downloaden achtergrondmanifest.

   * `INVALID_SEEK_WARNING` Wordt verzonden wanneer een zoekopdracht wordt uitgevoerd in een bereik dat niet doorzoekbaar is (in `nonSeekableRanges` instellen in `PTBlackoutMetadata`).
