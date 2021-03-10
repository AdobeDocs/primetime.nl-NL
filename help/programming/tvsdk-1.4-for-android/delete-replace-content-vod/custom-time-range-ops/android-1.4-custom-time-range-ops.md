---
description: TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.
title: Aangepaste tijdbereikbewerkingen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# Aangepaste tijdbereikbewerkingen {#custom-time-range-operations}

TVSDK ondersteunt het programmatisch verwijderen en vervangen van inhoud van advertenties in VOD-streams.

De functie Verwijderen en vervangen breidt de functie Aangepaste markeertekens uit. Met aangepaste advertenties worden secties van de hoofdinhoud gemarkeerd als periodes voor ad-gerelateerde inhoud. Naast het markeren van deze tijdwaaiers, kunt u ook tijdwaaiers schrappen en vervangen.

Verwijderen en vervangen van de toevoeging wordt geïmplementeerd met `TimeRange`-elementen die verschillende typen tijdbereiken in een VOD-stroom identificeren: markeren, verwijderen en vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.

Voor het verwijderen en vervangen van advertenties gebruikt TVSDK de volgende *aangepaste tijdbereikbewerking* modi:

* **MARK**
(Deze worden aangepaste advertentiemarkeringen genoemd in eerdere versies van TVSDK). Ze markeren de begin- en eindtijd voor advertenties die al in de VOD-stream zijn geplaatst. Wanneer er tijdbereikmarkeringen van het type MARK in de stream aanwezig zijn, wordt een eerste plaatsing van 
`Mode.MARK` wordt gegenereerd en opgelost door de  `CustomAdMarkersContentResolver`instantie. Er worden geen advertenties ingevoegd.

* ****
DELETEFor DELETE-tijdbereiken, een eerste 
`placementInformation` van type  `Mode.DELETE` wordt gecreeerd en door het overeenkomstige  `DeleteContentResolver`. `ContentRemoval` Dit is een nieuw element  `timelineOperation` dat de bereiken definieert die uit de tijdlijn moeten worden verwijderd. TVSDK gebruikt `removeByLocalTime` van de Adobe Video Engine (AVE) API om die bewerking te vergemakkelijken. Als er DELETE waaiers en Adobe Primetime en beslissingsmeta-gegevens (vroeger genoemd geworden Auditude) zijn, worden de waaiers eerst geschrapt, dan lost `AuditudeResolver` advertenties gebruikend de normale Adobe Primetime en beslissingswerkschema op.

* **Tijdbereik**
VERVANGEN of VERVANGEN, twee initiële 
`placementInformations` worden gemaakt, één  `Mode.DELETE` en één  `Mode.REPLACE`. Met `DeleteContentResolver` worden eerst de tijdbereiken verwijderd en vervolgens worden door de `AuditudeResolver` advertenties van de opgegeven `replaceDuration` in de tijdlijn ingevoegd. Als er geen `replaceDuration` is opgegeven, bepaalt de server wat er moet worden ingevoegd.

TVSDK biedt de volgende opties ter ondersteuning van deze bewerkingen met aangepaste tijdreeksen:

* Meerdere oplossingen voor inhoud

   Een stream kan meerdere inhoudsoplossers hebben op basis van de advertentiemodus en de metagegevens van de advertentie. Het gedrag verandert met verschillende combinaties van advertentiemodi en ad meta-gegevens.
* Meerdere initiële `PlacementInformations` De `DefaultMediaPlayer` maakt een lijst met initiële `PlacementInformations` op basis van de advertentiemodus en advertentiemetagegevens die door de `MediaPlayerClient` moeten worden opgelost.

* Nieuwe modus voor advertenties: Aangepaste tijdbereiken

   Advertenties worden geplaatst op basis van de gegevens van het Tijdbereik van een externe bron (zoals een JSON-bestand).