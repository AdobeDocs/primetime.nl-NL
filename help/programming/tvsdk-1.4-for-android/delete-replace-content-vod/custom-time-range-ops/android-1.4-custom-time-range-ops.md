---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
title: Aangepaste tijdbereikbewerkingen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Aangepaste tijdbereikbewerkingen {#custom-time-range-operations}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

Verwijderen en vervangen van advertenties wordt geïmplementeerd met `TimeRange` elementen die verschillende typen tijdbereiken in een VOD-stroom identificeren: markeren, verwijderen en vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.

Voor het verwijderen en vervangen van advertenties gebruikt TVSDK het volgende *aangepaste tijdbereikbewerking* modi:

* **MARK**
(Deze worden aangepaste advertentiemarkeringen genoemd in eerdere versies van TVSDK). Ze markeren de begin- en eindtijd voor advertenties die al in de VOD-stream zijn geplaatst. Wanneer er tijdbereikmarkeringen van het type MARK in de stream aanwezig zijn, wordt een eerste plaatsing van `Mode.MARK` wordt gegenereerd en opgelost door `CustomAdMarkersContentResolver`. Er worden geen advertenties ingevoegd.

* **DELETE**
Voor tijdbereiken van DELETE, een eerste `placementInformation` van het type `Mode.DELETE` wordt gemaakt en opgelost door het overeenkomstige `DeleteContentResolver`. `ContentRemoval` is een nieuwe `timelineOperation` Hiermee worden de bereiken gedefinieerd die uit de tijdlijn moeten worden verwijderd. TVSDK gebruikt `removeByLocalTime` van de Adobe Video Engine (AVE) API om die bewerking te vergemakkelijken. Als er DELETE waaiers en Adobe Primetime en beslissingsgegevens (vroeger genoemd geworden Auditude) zijn, worden de waaiers eerst geschrapt, dan `AuditudeResolver` Hiermee worden advertenties opgelost met de normale Adobe Primetime- en beslissingsworkflow.

* **VERVANGEN**
Voor de tijdbereiken van de VERVANGING, aanvankelijk twee `placementInformations` worden gemaakt, één `Mode.DELETE` en één `Mode.REPLACE`. De `DeleteContentResolver` verwijdert eerst de tijdbereiken en vervolgens de `AuditudeResolver` voegt advertenties in van de opgegeven `replaceDuration` in de tijdlijn. Indien niet `replaceDuration` wordt opgegeven, bepaalt de server wat moet worden ingevoegd.

TVSDK biedt de volgende opties ter ondersteuning van deze bewerkingen met aangepaste tijdreeksen:

* Meerdere oplossingen voor inhoud

  Een stream kan meerdere inhoudsoplossers hebben op basis van de advertentiemodus en de metagegevens van de advertentie. Het gedrag verandert met verschillende combinaties van advertentiemodi en ad meta-gegevens.
* Meerdere initiële waarden `PlacementInformations` De `DefaultMediaPlayer` maakt een lijst met initialen `PlacementInformations` op basis van de advertentiemodus en de metagegevens van de advertentie die door de `MediaPlayerClient`.

* Nieuwe modus voor advertenties: aangepaste tijdbereiken

  Advertenties worden geplaatst op basis van de gegevens van het Tijdbereik van een externe bron (zoals een JSON-bestand).
