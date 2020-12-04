---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-title: Aangepaste tijdbereikbewerkingen
title: Aangepaste tijdbereikbewerkingen
uuid: fb27f343-718d-444e-8fc1-5ae0be02557b
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Overzicht {#custom-time-range-operations-overview}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

De schrapping en de vervanging van de toevoeging worden uitgevoerd met douanemarkeringen die verschillende types van tijdwaaiers in een stroom VOD identificeren: markeren, verwijderen en vervangen. Voor elk aangepast tijdbereik kunt u bijbehorende bewerkingen uitvoeren, zoals het verwijderen of vervangen van advertentie-inhoud.

Voor het verwijderen en vervangen van advertenties bevat TVSDK de volgende *aangepaste tijdbereikbewerking* modi:

* MARK - verzendt `AdBreak` gebeurtenissen voor de duidelijke gebieden. (Dit werd `customAdMarker` genoemd in vorige versies van TVSDK.) In deze modus is invoeging niet toegestaan.

* DELETE - Voor deze modus gebruikt de toepassing de klasse `TimeRangeCollection` om tijdgebieden te definiëren voor C3 Ad Deletion. In deze modus is invoeging toegestaan.
* VERVANGEN - In deze modus vervangt de toepassing een `timeRange` door een Adobe Primetime en een besluit `AdBreak`. De vervangingsverrichting begint waar de C3 Ad schrapping voorkomt, en beëindigt op de aangegeven tijd (korter of langer dan de originele tijdwaaier).

TVSDK biedt de klasse `CustomRangesOpportunityGenerator` om plaatsingsmogelijkheden voor de bereiken MARK en DELETE te genereren. Voor de modus VERVANGEN genereert TVSDK twee plaatsingsmogelijkheden voor elk tijdbereik:

* `CustomRangeResolver` genereert plaatsingsmogelijkheden voor DELETE
* `AuditudeAdResolver` produceert plaatsingskansen voor TUSSENVOEGSEL.