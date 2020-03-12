---
description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
seo-description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
seo-title: De klassen MediaPlayer en MediaResource
title: De klassen MediaPlayer en MediaResource
uuid: 7393c320-7dbb-4580-9425-a735f9d03ef5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# De klassen MediaPlayer en MediaResource{#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

De bibliotheek van TVSDK verstrekt een eenvoudige manier om inhoud voor playback te laden en voor te bereiden door de `replaceCurrentItem` methode in de interface te gebruiken MediaPlayer. Deze methode ontvangt een instantie van de MediaResource-klasse als het enige invoerargument. De MediaResource-klasse bestaat uit de volgende informatie:

* Een URL die de locatie vertegenwoordigt van de inhoud die op het punt staat te worden geladen.
* Een type. Dit is het type inhoud dat wordt geladen.

   Dit is een eenvoudige opsomming in de `MediaResource` klasse die de typen inhoud definieert die door de MediaPlayer kunnen worden geladen. Mogelijke waarden zijn HLS en HDS. Elke waarde is gekoppeld aan de tekenreeks die de veelgebruikte bestandsextensies vertegenwoordigt, `m3u8` voor HLS en `f4m` voor HDS.
* Bepaalde metagegevens, een instantie van de `Metadata` klasse.

   Deze woordenboekachtige structuur kan aanvullende informatie bevatten over de inhoud die op het punt staat te worden geladen, zoals informatie over de alternatieve/advertentie-inhoud die in de hoofdinhoud moet worden geplaatst.

De metagegevens zijn het medium waarmee informatie die betrekking heeft op alternatieve inhoud, wordt doorgegeven aan TVSDK. De `Metadata` interface definieert de API voor een algemene sleutelwaardeopslag, waarbij zowel de sleutel als de waarde onbewerkte tekenreeksen zijn.
