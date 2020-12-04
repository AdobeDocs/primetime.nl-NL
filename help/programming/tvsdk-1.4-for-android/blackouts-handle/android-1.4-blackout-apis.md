---
description: U kunt stroomstoringen in live videostreams verwerken en tijdens een stroomstoring alternatieve inhoud bieden.
seo-description: U kunt stroomstoringen in live videostreams verwerken en tijdens een stroomstoring alternatieve inhoud bieden.
seo-title: API-elementen voor doorbraak
title: API-elementen voor doorbraak
uuid: 263a8987-0c85-493a-9352-9605c877ba65
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# API-elementen voor uitchecken{#blackout-api-elements}

U kunt stroomstoringen in live videostreams verwerken en tijdens een stroomstoring alternatieve inhoud bieden.

Wanneer een brainstormsessie plaatsvindt in een live stream, gebruikt de speler gebeurtenishandlers om de brainstormsessie te detecteren en biedt deze gebruikers alternatieve inhoud die niet in aanmerking komen om de hoofdstream te bekijken. De speler detecteert het begin en einde van de periode van stroomuitval, schakelt het afspelen van de hoofdstream over naar een alternatieve stream en schakelt terug naar de hoofdstream wanneer de periode van stroomuitval eindigt.

Stroomuitval in live streams afhandelen:

1. Stel uw app in om black-out-tags te detecteren door u te abonneren op black-out-tags in een live-streaming manifest.

   TVSDK detecteert alleen geen black-out-tags; u moet zich abonneren op brainstormtags om meldingen te ontvangen wanneer de tags tijdens het parseren van manifestbestanden worden aangetroffen.
1. Maak gebeurtenislisteners voor tags waarop de speler is geabonneerd (in dit geval de tags PLAYBACK en BLACKOUTS).

   Wanneer een tag voorkomt waarop de speler heeft geabonneerd (bijvoorbeeld een black-out tag) in de manifests van de voorgrond- (hoofdinhoud) of de achtergrond- (alternatieve inhoud), verzendt TVSDK een `TimedMetadataEvent` en maakt een `TimedMetadataObject` voor `TimedMetadataEvent`.

1. Implementeer handlers voor de getimede metagegevensgebeurtenissen voor zowel de voorgrond- als de achtergrondstreams.

   In deze handlers, krijg de begin en eindtijden voor de zwartoutperiode van de getimed voorwerpen van de meta-gegevensgebeurtenis.
1. Methoden maken voor het schakelen tussen inhoud aan het begin en einde van de periode van uitnemen.

   Wanneer de brainstormperiode begint, schakelt u de hoofdinhoud over naar de achtergrond en schakelt u de alternatieve inhoud om als de hoofdstream te worden. Ga door met het ophalen en parseren van het oorspronkelijke manifest op de achtergrond en blijf controleren op de tag &quot;black-out end&quot;, zodat de speler zich opnieuw bij de oorspronkelijke stream kan aansluiten wanneer de black-out eindigt.
1. Werk niet-doorzoekbare bereiken bij als het bereik van de stroomstoring zich in DVR op de afspeelstream bevindt.

   Volg en behandel de `TimedMetadata` op de achtergrondstroom, door black-out niet-doorzoekbare bereiken voor te bereiden en bij te werken.

TVSDK biedt API-elementen die nuttig zijn bij het implementeren van stroomonderbrekingen, zoals methoden, metagegevens en meldingen.

U kunt het volgende gebruiken wanneer het uitvoeren van een stroomoplossing in uw speler.

* **MediaPlayer**

   * `registerCurrentItemAsBackgroundItem` Hiermee slaat u de momenteel geladen bron op als de achtergrondbron. Als `replaceCurrentResource` na deze methode wordt geroepen, blijft TVSDK manifest van het achtergrondpunt downloaden tot u `unregisterCurrentBackgroundItem`, `release`, of `reset` roept.

   * `unregisterCurrentBackgroundItem` Stelt het achtergronditem in op null en stopt het ophalen en parseren van het achtergrondmanifest.

* **BlackoutMetadata** -

   Een klasse Metadata die specifiek is voor black-outs.

   Hierdoor kunt u niet-doorzoekbare bereiken instellen (een array van `TimeRanges`) op TVSDK. TVSDK controleert deze waaiers telkens als de gebruiker zoekt. Als deze is ingesteld en de gebruiker een bereik zoekt dat niet kan worden doorzocht, dwingt TVSDK de viewer tot het einde van het bereik dat niet kan worden doorzocht.

* **START HIER VOLGENDE** AdvertisingMetadataEnable of disable preroll op een levende stroom door  `enableLivePreroll` aan waar of vals te plaatsen. Indien onwaar, maakt TVSDK geen expliciete vraag van de advertentieserver naar pre-rol advertenties vóór de inhoudsplayback en zo speelt niet pre-rol. Dit heeft geen invloed op de middenrollen. De standaardwaarde is true.

* **MediaPlayer.BlackoutsEventListener**

   * `onTimedMetadataInBackgroundItem` - Wordt verzonden wanneer een geabonneerde tag in het achtergrondmanifest wordt gedetecteerd en er een nieuwe  `TimedMetadata` instantie uit wordt voorbereid. De instantie `TimedMetadata` wordt verzonden als parameter.

   * `onBackgroundManifestFailed` - Wordt verzonden wanneer de mediaspeler het achtergrondmanifest volledig niet laadt, dat wil zeggen dat alle stream-URL&#39;s een fout of een ongeldige reactie retourneren.

* **Meldingen**

   * `BACKGROUND_MANIFEST_WARNING`

      * Code: 204000
      * Type: Waarschuwing
      * Fout in downloaden achtergrondmanifest.