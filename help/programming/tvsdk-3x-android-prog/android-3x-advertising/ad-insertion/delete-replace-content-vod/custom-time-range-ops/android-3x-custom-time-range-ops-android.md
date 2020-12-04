---
description: De klasse CustomRangeMetadata identificeert verschillende typen tijdbereiken in een VOD-streammarkering, -verwijderen en -vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.
seo-description: De klasse CustomRangeMetadata identificeert verschillende typen tijdbereiken in een VOD-streammarkering, -verwijderen en -vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.
seo-title: Aangepaste tijdbereikbewerkingen
title: Aangepaste tijdbereikbewerkingen
uuid: eadd4d8d-0e03-40ca-ae3b-eede82bf2df8
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Aangepaste tijdbereikbewerkingen {#custom-time-range-operations}

De klasse CustomRangeMetadata identificeert verschillende typen tijdbereiken in een VOD-stream: markeren, verwijderen en vervangen. Voor elk van deze types van douanetijdwaaier, kunt u overeenkomstige verrichtingen uitvoeren, met inbegrip van het schrappen en het vervangen van advertentie inhoud.

<!--<a id="section_1323C0BAC259424C85A6ACFB48FE77EC"></a>-->

Voor het verwijderen en vervangen van advertenties gebruikt TVSDK de volgende *aangepaste tijdbereikbewerking* modi:

* **** MARKTThis mode werd bedoeld als douane en tellers in vorige versies van TVSDK. De modus markeert de begin- en eindtijd voor advertenties die al in de VOD-stream zijn geplaatst. Wanneer er tijdbereikmarkeringen van het type `MARK` in de stream aanwezig zijn, wordt een eerste plaatsing van `Mode.MARK` gegenereerd door `CustomMarkerOpportunityGenerator` en opgelost door `CustomRangeResolver`. Er worden geen advertenties ingevoegd.

* **** DELETEFor  `DELETE` tijdwaaiers,  `placementInformation` wordt een eerste  `Mode.DELETE` van type gecreeerd en opgelost door  `CustomRangeResolver`. `DeleteRangeTimelineOperation` definieert de bereiken die uit de tijdlijn moeten worden verwijderd en TVSDK gebruikt  `removeByLocalTime` de API Adobe Video Engine (AVE) om deze bewerking te voltooien. Als er DELETE waaiers en Adobe Primetime en beslissingsmeta-gegevens zijn, worden de waaiers eerst geschrapt, dan lost `AuditudeResolver` advertenties gebruikend de typische Adobe Primetime en beslissingswerkschema op.

* **** REPLACEFor  `REPLACE` time range, twee initial  `placementInformations` worden gecreeerd, één  `Mode.DELETE` en één  `Mode.REPLACE`. `CustomRangeResolver` Hiermee verwijdert u eerst de tijdbereiken en voegt u vervolgens de  `AuditudeResolver` advertenties van de opgegeven  `replaceDuration` tijdlijn in. Als er geen `replaceDuration` is opgegeven, bepaalt de server wat er moet worden ingevoegd.

TVSDK biedt de volgende opties ter ondersteuning van deze bewerkingen met aangepaste tijdreeksen:

* Meerdere oplossingen voor inhoud

   Een stream kan meerdere inhoudsoplossers hebben op basis van de advertentiemodus en de metagegevens van de advertentie. Het gedrag verandert met verschillende combinaties van advertentiemodi en ad meta-gegevens.
* Meerdere initiële mogelijkheden met `CustomMarkerOpportunityGenerator`.
* Een nieuwe ad signaalwijze, `CUSTOM_RANGES`.

   Advertenties worden geplaatst op basis van de gegevens van het Tijdbereik van een externe bron, zoals een JSON-bestand.