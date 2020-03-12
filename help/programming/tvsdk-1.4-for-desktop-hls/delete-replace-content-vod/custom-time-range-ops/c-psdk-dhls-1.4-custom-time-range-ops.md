---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-title: Aangepaste tijdbereikbewerkingen
title: Aangepaste tijdbereikbewerkingen
uuid: fb27f343-718d-444e-8fc1-5ae0be02557b
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Overzicht {#custom-time-range-operations-overview}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

De schrapping en de vervanging van de toevoeging worden uitgevoerd met douanemarkeringen die verschillende types van tijdwaaiers in een stroom VOD identificeren: markeren, verwijderen en vervangen. Voor elk aangepast tijdbereik kunt u bijbehorende bewerkingen uitvoeren, zoals het verwijderen of vervangen van advertentie-inhoud.

Voor het verwijderen en vervangen van advertenties bevat TVSDK de volgende bewerkingsmodi voor het *aangepaste tijdbereik* :

* MARK - hiermee verzendt u `AdBreak` gebeurtenissen voor de gemarkeerde gebieden. (Dit werd aangeroepen `customAdMarker` in eerdere versies van TVSDK.) In deze modus is invoeging niet toegestaan.

* VERWIJDEREN - Voor deze modus gebruikt de app de `TimeRangeCollection` klasse om tijdgebieden voor verwijderen van C3 en ADT te definiëren. In deze modus is invoeging toegestaan.
* VERVANGEN - In deze modus vervangt de app een `timeRange` bestand door een Adobe Primetime-beslissing `AdBreak`. De vervangingsverrichting begint waar de C3 Ad schrapping voorkomt, en beëindigt op de aangegeven tijd (korter of langer dan de originele tijdwaaier).

TVSDK biedt een `CustomRangesOpportunityGenerator` klasse om plaatsingsmogelijkheden voor de bereiken MARK en DELETE te genereren. Voor de modus VERVANGEN genereert TVSDK twee plaatsingsmogelijkheden voor elk tijdbereik:

* De `CustomRangeResolver` genereert plaatsingsmogelijkheden voor DELETE
* Het `AuditudeAdResolver` produceert plaatsingskansen voor TUSSENVOEGSEL.