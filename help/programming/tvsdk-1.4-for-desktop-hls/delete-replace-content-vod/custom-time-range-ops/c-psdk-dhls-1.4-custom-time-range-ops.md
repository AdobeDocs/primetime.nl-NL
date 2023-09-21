---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
title: Aangepaste tijdbereikbewerkingen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Overzicht {#custom-time-range-operations-overview}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

Verwijderen en vervangen van toevoegingen worden geïmplementeerd met aangepaste markeringen die verschillende typen tijdbereiken in een VOD-stroom identificeren: markering, verwijderen en vervangen. Voor elk aangepast tijdbereik kunt u bijbehorende bewerkingen uitvoeren, zoals het verwijderen of vervangen van advertentie-inhoud.

Voor het verwijderen en vervangen van advertenties bevat TVSDK het volgende: *aangepaste tijdbereikbewerking* modi:

* MARK - Verzendingen `AdBreak` gebeurtenissen voor de gemarkeerde gebieden. (Dit heet `customAdMarker` in eerdere versies van TVSDK.) In deze modus is invoeging niet toegestaan.

* DELETE - Voor deze modus gebruikt de app de opdracht `TimeRangeCollection` -klasse om tijdgebieden te definiëren voor verwijderen van C3 en toevoegen. In deze modus is invoeging toegestaan.
* VERVANGEN - In deze modus vervangt de app een `timeRange` met een Adobe Primetime-besluit `AdBreak`. De vervangingsverrichting begint waar de C3 Ad schrapping voorkomt, en beëindigt op de aangegeven tijd (korter of langer dan de originele tijdwaaier).

TVSDK biedt een `CustomRangesOpportunityGenerator` -klasse om plaatsingsmogelijkheden voor de bereiken MARK en DELETE te genereren. Voor de modus VERVANGEN genereert TVSDK twee plaatsingsmogelijkheden voor elk tijdbereik:

* De `CustomRangeResolver` genereert plaatsingsmogelijkheden voor DELETE
* De `AuditudeAdResolver` genereert plaatsingsmogelijkheden voor INSERT.
