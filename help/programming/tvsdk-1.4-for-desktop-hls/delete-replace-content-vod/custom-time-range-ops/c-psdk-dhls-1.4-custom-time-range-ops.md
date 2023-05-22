---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
title: Aangepaste tijdbereikbewerkingen
exl-id: 5480b22a-ecff-4fd8-9ec0-40e4a2e97641
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Overzicht {#custom-time-range-operations-overview}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

<!--<a id="section_D3FE668CAF764DCC912373D5410C932C"></a>-->

De schrapping en de vervanging van de toevoeging worden uitgevoerd met douanemarkeringen die verschillende types van tijdwaaiers in een stroom VOD identificeren: markeren, verwijderen en vervangen. Voor elk aangepast tijdbereik kunt u bijbehorende bewerkingen uitvoeren, zoals het verwijderen of vervangen van advertentie-inhoud.

Voor het verwijderen en vervangen van advertenties bevat TVSDK het volgende: *aangepaste tijdbereikbewerking* modi:

* MARK - Verzendingen `AdBreak` gebeurtenissen voor de gemarkeerde gebieden. (Dit heet `customAdMarker` in eerdere versies van TVSDK.) In deze modus is invoeging niet toegestaan.

* DELETE - Voor deze modus gebruikt de app de opdracht `TimeRangeCollection` -klasse om tijdgebieden te definiëren voor verwijderen van C3 en toevoegen. In deze modus is invoeging toegestaan.
* VERVANGEN - In deze modus vervangt de app een `timeRange` met een Adobe Primetime-besluit `AdBreak`. De vervangingsverrichting begint waar de C3 Ad schrapping voorkomt, en beëindigt op de aangegeven tijd (korter of langer dan de originele tijdwaaier).

TVSDK biedt een `CustomRangesOpportunityGenerator` -klasse om plaatsingsmogelijkheden voor de bereiken MARK en DELETE te genereren. Voor de modus VERVANGEN genereert TVSDK twee plaatsingsmogelijkheden voor elk tijdbereik:

* De `CustomRangeResolver` genereert plaatsingsmogelijkheden voor DELETE
* De `AuditudeAdResolver` genereert plaatsingsmogelijkheden voor INSERT.
