---
description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
title: De klassen MediaPlayer en MediaResource
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# De klassen van MediaPlayer en MediaResource{#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

De bibliotheek van TVSDK verstrekt een eenvoudige manier om inhoud voor playback te laden en voor te bereiden door de `replaceCurrentItem` methode in de interface te gebruiken MediaPlayer. Deze methode ontvangt een instantie van de MediaResource-klasse als het enige invoerargument. De MediaResource-klasse bestaat uit de volgende informatie:

* Een URL die de locatie vertegenwoordigt van de inhoud die op het punt staat te worden geladen.
* Een type. Dit is het type inhoud dat wordt geladen.

   Dit is een eenvoudige opsomming in de klasse `MediaResource` die de typen inhoud definieert die door de MediaPlayer kunnen worden geladen. Mogelijke waarden zijn HLS en HDS. Elke waarde is gekoppeld aan de tekenreeks die de veelgebruikte bestandsextensies vertegenwoordigt, `m3u8` voor HLS en `f4m` voor HDS.
* Sommige metagegevens, die een instantie zijn van de klasse `Metadata`.

   Deze woordenboekachtige structuur kan aanvullende informatie bevatten over de inhoud die op het punt staat te worden geladen, zoals informatie over de alternatieve/advertentie-inhoud die in de hoofdinhoud moet worden geplaatst.

De metagegevens zijn het medium waarmee informatie die betrekking heeft op alternatieve inhoud, wordt doorgegeven aan TVSDK. De `Metadata` interface bepaalt API voor een generische zeer belangrijk-waardeopslag, waar zowel de sleutel als de waarde duidelijke koorden zijn.
