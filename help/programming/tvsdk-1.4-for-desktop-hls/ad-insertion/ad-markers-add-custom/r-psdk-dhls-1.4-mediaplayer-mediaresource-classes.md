---
description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
title: De klassen MediaPlayer en MediaResource
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# De klassen van MediaPlayer en MediaResource{#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

De bibliotheek TVSDK biedt een eenvoudige manier om inhoud te laden en voor te bereiden voor afspelen met de methode `replaceCurrentResource` in de interface `MediaPlayer`. Deze methode ontvangt een instantie van de klasse `MediaResource` als enig inputargument. De klasse `MediaResource` bestaat uit de volgende informatie:

* Een URL die de locatie vertegenwoordigt van de inhoud die op het punt staat te worden geladen.
* Een type. Dit is het type inhoud dat wordt geladen.

   Dit is een tekenreeks die de typen inhoud definieert die door de `MediaPlayer` kunnen worden geladen. Mogelijke waarden zijn HLS en HDS. Elke waarde is gekoppeld aan de tekenreeks die de veelgebruikte bestandsextensies vertegenwoordigt, &quot;m3u8&quot; voor HLS en &quot;f4m&quot; voor HDS.
* Sommige metagegevens, die een instantie zijn van de klasse `Metadata`.

   Deze woordenboekachtige structuur kan aanvullende informatie bevatten over de inhoud die op het punt staat te worden geladen, zoals informatie over de alternatieve/advertentie-inhoud die in de hoofdinhoud moet worden geplaatst.

De metagegevens zijn het medium waarmee informatie die betrekking heeft op alternatieve inhoud, wordt doorgegeven aan TVSDK. De `Metadata` interface bepaalt API voor een generische zeer belangrijk-waardeopslag, waar zowel de sleutel als de waarde duidelijke koorden zijn.
