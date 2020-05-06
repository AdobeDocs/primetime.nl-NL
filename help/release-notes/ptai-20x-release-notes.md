---
title: Opmerkingen bij de release PTAI 20.3.3
description: In de opmerkingen bij de release van PTAI 20.5.1 wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in de dynamische invoeging van Primetime in 2020.
translation-type: tm+mt
source-git-commit: 2a5866be64895ba13994720bf943dc676c2595bf
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Opmerkingen bij de release Primetime Dynamic AD 20.5.1

Opmerkingen bij de release Dynamische advertentie 20.5.1 beschrijven wat nieuw of gewijzigd is, problemen die zijn opgelost en bekende problemen in Dynamische advertentie invoegen in Primetime in 2020.

## Nieuwe functies in PTAI 20.5.1

**Wanneer:** Dinsdag 5 mei 2020, 04.00 - 05.00 UUR OOSTEN

* Probleem verholpen om ervoor te zorgen dat de juiste CORS-koppen worden opgegeven wanneer if-Modified-Since-koppen worden verzonden.

* Bugfixes op het CRS-dashboard.

* Onderhoudsupdates.

## Wat veranderde in vorige versies

### Versie 20.3.4

**Wanneer:** Woensdag 1 april 2020, 03.00 - 04.00 UUR OOSTEN

* Probleem verholpen waarbij ondertitels niet meer gesynchroniseerd werden na het plaatsen van de advertentie in VOD/WebVTT.

* Beveiligingsupdates.

### Versie 20.3.3

**Wanneer:** Donderdag 26 maart 2020, 3.00 uur tot 4.00 uur OOSTENRIJK

* SSAI 4XX en 5XX antwoorden verstrekken nu correct CORS-verwante kopballen, toestaand dwars-domein javascript/webview cliënten om foutenreacties met succes te lezen.

* Probleem verholpen met X-Forwarded-For headers, waarbij IPv6-adressen niet correct URL-gecodeerd waren wanneer ze aan de advertentieservers werden doorgegeven.

* Probleem verholpen met CMAF/gedemuxed audiostreams, waarbij in bepaalde scenario&#39;s de EXT-X-MEDIA-SEQUENTIE-nummers onjuist zouden stijgen.

### Versie 20.1.3

**Wanneer:** Dinsdag 28 januari 2020, 14.00 tot 3.00 uur OOSTENRIJK

* **VMAP met FER-ondersteuning voor &quot;nbc&quot; CueFormat** Convert cues van FER-stream naar FW-tijdlijnoverschrijvingsparams, wanneer ptcueformat=nbc wordt gebruikt en de stream een VOD-stream is met in-manifest aanwijzingen en kant-en-klare advertenties.

* Maak user-agent gebied in de Kopbal van HTTP alvorens aan derde Ad providers/CDN door:sturen.

* Filter besturings- en niet-afdrukbare tekens (ascii-code &lt; 32) uit HTTP-headers &quot;user-agent&quot; voordat u deze verzendt naar Auditude en andere advertentieproviders, CDN&#39;s. Auditude Ad-Call gebruikt om voor dergelijke ongeldige kopballen te ontbreken.

* Verwijder oude V1-objecten van NetStorage-groepen om het aantal objecten binnen de veilige grenzen van Akamai te houden.

## Opgeloste problemen

Wanneer de oplossing aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond. Bijvoorbeeld ZD#xxxxx.

**PTAI 20.3.3**

* Probleem met X-Forwarded-For kopballen, waar IPv6 adressen niet correct URL gecodeerd wanneer overgegaan tot de advertentieservers waren.

* Probleem met CMAF/gedemuxed audiostromen, waar in bepaalde scenario&#39;s de aantallen EXT-X-MEDIA-REEKS in bepaalde scenario&#39;s verkeerd stijgen

## Bekende problemen en beperkingen

**PTAI 20.3.3**

Geen nieuwe beperking toegevoegd.
