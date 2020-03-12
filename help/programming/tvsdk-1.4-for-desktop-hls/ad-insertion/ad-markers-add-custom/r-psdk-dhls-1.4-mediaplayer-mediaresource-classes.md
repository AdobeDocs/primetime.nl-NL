---
description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
seo-description: Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.
seo-title: De klassen MediaPlayer en MediaResource
title: De klassen MediaPlayer en MediaResource
uuid: 36ef75f3-08f7-4fc5-88a7-9bab9198b917
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# De klassen MediaPlayer en MediaResource{#mediaplayer-and-mediaresource-classes}

Een MediaResource vertegenwoordigt de inhoud die op het punt staat door de instantie MediaPlayer te worden geladen.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

De bibliotheek van TVSDK verstrekt een eenvoudige manier om inhoud voor playback te laden en voor te bereiden door de `replaceCurrentResource` methode in de `MediaPlayer` interface te gebruiken. Deze methode ontvangt een instantie van de `MediaResource` klasse als het enige invoerargument. De `MediaResource` klasse bestaat uit de volgende informatie:

* Een URL die de locatie vertegenwoordigt van de inhoud die op het punt staat te worden geladen.
* Een type. Dit is het type inhoud dat wordt geladen.

   Dit is een tekenreeks die de typen inhoud definieert die door de `MediaPlayer`instantie kunnen worden geladen. Mogelijke waarden zijn HLS en HDS. Elke waarde is gekoppeld aan de tekenreeks die de veelgebruikte bestandsextensies vertegenwoordigt, &quot;m3u8&quot; voor HLS en &quot;f4m&quot; voor HDS.
* Bepaalde metagegevens, een instantie van de `Metadata` klasse.

   Deze woordenboekachtige structuur kan aanvullende informatie bevatten over de inhoud die op het punt staat te worden geladen, zoals informatie over de alternatieve/advertentie-inhoud die in de hoofdinhoud moet worden geplaatst.

De metagegevens zijn het medium waarmee informatie die betrekking heeft op alternatieve inhoud, wordt doorgegeven aan TVSDK. De `Metadata` interface definieert de API voor een algemene sleutelwaardeopslag, waarbij zowel de sleutel als de waarde onbewerkte tekenreeksen zijn.
