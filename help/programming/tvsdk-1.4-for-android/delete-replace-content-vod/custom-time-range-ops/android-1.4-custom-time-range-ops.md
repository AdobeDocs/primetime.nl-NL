---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
seo-title: Aangepaste tijdbereikbewerkingen
title: Aangepaste tijdbereikbewerkingen
uuid: e04af786-8dac-41a6-8406-f2ca04f612a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Aangepaste tijdbereikbewerkingen {#custom-time-range-operations}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

De schrapping en de vervanging van de toevoeging wordt uitgevoerd met `TimeRange` elementen die verschillende types van tijdwaaiers in een stroom VOD identificeren: markeren, verwijderen en vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.

Voor het verwijderen en vervangen van advertenties gebruikt TVSDK de volgende bewerkingsmodi voor het *aangepaste tijdbereik* :

* **MARK**(Deze worden aangepaste advertentiemarkeringen genoemd in eerdere versies van TVSDK). Ze markeren de begin- en eindtijd voor advertenties die al in de VOD-stream zijn geplaatst. Wanneer er tijdbereikmarkeringen van het type MARK in de stream staan, `Mode.MARK` wordt een eerste plaatsing van gegenereerd en opgelost door de `CustomAdMarkersContentResolver`. Er worden geen advertenties ingevoegd.

* **DELETE** For DELETE-tijdbereiken, an initial `placementInformation` of type `Mode.DELETE` is created and resolved by the corresponding `DeleteContentResolver`. `ContentRemoval` Dit is een nieuw element `timelineOperation` dat de bereiken definieert die uit de tijdlijn moeten worden verwijderd. TVSDK maakt gebruik `removeByLocalTime` van de API (Adobe Video Engine, AVE) om deze bewerking te vergemakkelijken. Als er DELETE-bereiken en Adobe Primetime- en beslissingsmetagegevens (voorheen Auditude) zijn, worden de bereiken eerst verwijderd, waarna de `AuditudeResolver` advertenties worden opgelost met de normale Adobe Primetime- en beslissingsworkflow.

* **REPLACE** For REPLACE time range, two initial `placementInformations` wordt gecreeerd, één `Mode.DELETE` en één `Mode.REPLACE`. De `DeleteContentResolver` tijdbereiken worden eerst verwijderd en vervolgens worden de `AuditudeResolver` invoegingen van het opgegeven object `replaceDuration` in de tijdlijn ingevoegd. Als er geen waarde `replaceDuration` is opgegeven, bepaalt de server wat er moet worden ingevoegd.

TVSDK biedt de volgende opties ter ondersteuning van deze bewerkingen met aangepaste tijdreeksen:

* Meerdere oplossingen voor inhoud

   Een stream kan meerdere inhoudsoplossers hebben op basis van de advertentiemodus en de metagegevens van de advertentie. Het gedrag verandert met verschillende combinaties van advertentiemodi en ad meta-gegevens.
* Meerdere initiële `PlacementInformations` The `DefaultMediaPlayer` maakt een lijst met eerste gegevens `PlacementInformations` op basis van de verzendmodus en de metagegevens voor advertenties die door de `MediaPlayerClient`gebruiker moeten worden opgelost.

* Nieuwe modus voor advertenties: Aangepaste tijdbereiken

   Advertenties worden geplaatst op basis van de gegevens van het Tijdbereik van een externe bron (zoals een JSON-bestand).