---
description: De klasse CustomRangeMetadata identificeert verschillende typen tijdbereiken in een VOD-streammarkering, -verwijderen en -vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.
title: Aangepaste tijdbereikbewerkingen
exl-id: ae457ee6-5649-469b-b5f1-1e0b16b6eb9c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Aangepaste tijdbereikbewerkingen {#custom-time-range-operations}

De klasse CustomRangeMetadata identificeert verschillende typen tijdbereiken in een VOD-stream: markeren, verwijderen en vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Voor het verwijderen en vervangen van advertenties gebruikt TVSDK het volgende *aangepaste tijdbereikbewerking* modi:

* **MARK** Deze modus werd in eerdere versies van TVSDK aangeduid als aangepaste advertentiemarkeringen. De modus markeert de begin- en eindtijd voor advertenties die al in de VOD-stream zijn geplaatst. Wanneer er tekstbereikmarkeringen zijn `MARK` in de stream, een eerste plaatsing van `Mode.MARK` wordt gegenereerd door `CustomMarkerOpportunityGenerator` en opgelost door `CustomRangeResolver`. Er worden geen advertenties ingevoegd.

* **DELETE** Voor `DELETE` tijdbereiken, een eerste `placementInformation` van het type `Mode.DELETE` wordt gemaakt en opgelost door `CustomRangeResolver`. `DeleteRangeTimelineOperation` definieert de bereiken die uit de tijdlijn moeten worden verwijderd en TVSDK gebruikt `removeByLocalTime` van de Adobe Video Engine (AVE) API om deze bewerking te voltooien. Als er DELETE waaiers en Adobe Primetime en beslissingsmeta-gegevens zijn, worden de waaiers eerst geschrapt, dan `AuditudeResolver` Hiermee worden advertenties opgelost met de gebruikelijke Adobe Primetime- en beslissingsworkflow.

* **VERVANGEN** Voor `REPLACE` tijdbereiken, twee initiële `placementInformations` worden gemaakt, één `Mode.DELETE` en één `Mode.REPLACE`. `CustomRangeResolver` verwijdert eerst de tijdbereiken en vervolgens de `AuditudeResolver` voegt advertenties in van de opgegeven `replaceDuration` in de tijdlijn. Indien niet `replaceDuration` wordt opgegeven, bepaalt de server wat moet worden ingevoegd.

TVSDK biedt de volgende opties ter ondersteuning van deze bewerkingen met aangepaste tijdreeksen:

* Meerdere oplossingen voor inhoud

   Een stream kan meerdere inhoudsoplossers hebben op basis van de advertentiemodus en de metagegevens van de advertentie. Het gedrag verandert met verschillende combinaties van advertentiemodi en ad meta-gegevens.
* Meerdere initiële mogelijkheden met `CustomMarkerOpportunityGenerator`.
* een nieuwe ad-signaalmodus, `CUSTOM_RANGES`.

   Advertenties worden geplaatst op basis van de gegevens van het Tijdbereik van een externe bron, zoals een JSON-bestand.
