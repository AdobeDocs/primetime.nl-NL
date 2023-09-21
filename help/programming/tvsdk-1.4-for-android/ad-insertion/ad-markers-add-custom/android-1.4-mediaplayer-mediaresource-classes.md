---
description: Een MediaResource vertegenwoordigt de inhoud die door de instantie MediaPlayer wordt geladen.
title: De klassen MediaPlayer en MediaResource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# De klassen MediaPlayer en MediaResource{#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die door de instantie MediaPlayer wordt geladen.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

De TVSDK-bibliotheek biedt een eenvoudige manier om inhoud te laden en voor te bereiden voor afspelen met behulp van de `replaceCurrentItem` in de MediaPlayer-interface. Deze methode ontvangt een instantie van de MediaResource-klasse als het enige invoerargument. De MediaResource-klasse bestaat uit de volgende informatie:

* Een URL die de locatie vertegenwoordigt van de inhoud die op het punt staat te worden geladen.
* Een type. Dit is het type inhoud dat wordt geladen.

  Dit is een eenvoudige opsomming in het dialoogvenster `MediaResource` klasse die de typen inhoud definieert die door de MediaPlayer kunnen worden geladen. Mogelijke waarden zijn HLS en HDS. Elke waarde is gekoppeld aan de tekenreeks die de veelgebruikte bestandsextensies vertegenwoordigt. `m3u8` voor HLS en `f4m` voor HDS.
* Sommige metagegevens, die een instantie zijn van de `Metadata` klasse.

  Deze woordenboekachtige structuur kan aanvullende informatie bevatten over de inhoud die op het punt staat te worden geladen, zoals informatie over de alternatieve/advertentie-inhoud die in de hoofdinhoud moet worden geplaatst.

De metagegevens zijn het medium waarmee informatie die betrekking heeft op alternatieve inhoud, wordt doorgegeven aan TVSDK. De `Metadata` De interface definieert de API voor een algemene sleutelwaardeopslag, waarbij zowel de sleutel als de waarde onbewerkte tekenreeksen zijn.
