---
description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
title: De klassen MediaPlayer en MediaResource
exl-id: c431c9f9-98a3-402c-b799-450f30f668dd
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# De klassen MediaPlayer en MediaResource{#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

De TVSDK-bibliotheek biedt een eenvoudige manier om inhoud te laden en voor te bereiden voor afspelen met behulp van de `replaceCurrentResource` in de `MediaPlayer` interface. Deze methode ontvangt een instantie van de `MediaResource` -klasse als het enige invoerargument. De `MediaResource` klasse bestaat uit de volgende informatie:

* Een URL die de locatie vertegenwoordigt van de inhoud die op het punt staat te worden geladen.
* Een type. Dit is het type inhoud dat wordt geladen.

   Dit is een tekenreeks die de typen inhoud definieert die kunnen worden geladen door de `MediaPlayer`. Mogelijke waarden zijn HLS en HDS. Elke waarde is gekoppeld aan de tekenreeks die de veelgebruikte bestandsextensies vertegenwoordigt, &quot;m3u8&quot; voor HLS en &quot;f4m&quot; voor HDS.
* Sommige metagegevens, die een instantie zijn van de `Metadata` klasse.

   Deze woordenboekachtige structuur kan aanvullende informatie bevatten over de inhoud die op het punt staat te worden geladen, zoals informatie over de alternatieve/advertentie-inhoud die in de hoofdinhoud moet worden geplaatst.

De metagegevens zijn het medium waarmee informatie die betrekking heeft op alternatieve inhoud, wordt doorgegeven aan TVSDK. De `Metadata` De interface definieert de API voor een algemene sleutelwaardeopslag, waarbij zowel de sleutel als de waarde onbewerkte tekenreeksen zijn.
