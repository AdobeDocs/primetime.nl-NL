---
title: Opmerkingen bij de release PTAI 20.5.1
description: In de opmerkingen bij de release van PTAI 20.5.1 wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in de dynamische invoeging van Primetime in 2020.
translation-type: tm+mt
source-git-commit: 9c117678a049e34bfcf960e992a4ce7361968f3e
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Opmerkingen bij de release Primetime Dynamic AD 20.5.1

Opmerkingen bij de release Dynamische advertentie 20.5.1 beschrijven wat nieuw of gewijzigd is, problemen die zijn opgelost en bekende problemen in Dynamische advertentie invoegen in Primetime in 2020.

## Nieuwe functies in PTAI 20.5.1

**Wanneer:** Dinsdag 5 mei 2020, 04.00 - 05.00 uur Oosterse tijd

* Probleem verholpen om ervoor te zorgen dat correcte kopballen CORS worden verstrekt wanneer if-Modified-Since kopballen worden verzonden.

* Bugfixes op het CRS-dashboard.

* Onderhoudsupdates.

## Wat veranderde in vorige versies

### Versie 20.3.4

**Wanneer:** Woensdag 1 april 2020, 03.00 - 04.00 uur Oosterse tijd

* Probleem verholpen waarbij ondertitels niet meer gesynchroniseerd werden na het plaatsen van de advertentie in VOD/WebVTT.

* Beveiligingsupdates.

### Versie 20.3.3

**Wanneer:** Donderdag 26 maart 2020, 03.00 - 04.00 uur Oosterse tijd

* SSAI 4XX en 5XX antwoorden verstrekken nu correct CORS-verwante kopballen, toestaand dwars-domein javascript/webview cliënten om foutenreacties met succes te lezen.

* Probleem verholpen met X-Forwarded-For headers, waarbij IPv6-adressen niet correct URL-gecodeerd waren wanneer ze aan de advertentieservers werden doorgegeven.

* Probleem verholpen met CMAF/gedemuxed audiostreams, waarbij in bepaalde scenario&#39;s de EXT-X-MEDIA-SEQUENTIE-nummers onjuist zouden stijgen.

### Versie 20.3.2

**Wanneer:** Woensdag 11 maart 2020, 05.30 - 07.00 uur Oosterse tijd

* Verbeteringen aan SCTE35 signaalbehandeling.

* Onderhoudsupdates.

### Versie 20.3.1

**Wanneer:** Donderdag 5 maart 2020, 20.30 uur tot 04.30 uur Oosterse tijd

* Prestatieverbeteringen:

   * Extra cacheondersteuning voor zowel master-/media m3u8-manifests. Deze manifests antwoorden nu aan geheime voorgeheugen-controle: de openbare en Max-Leeftijd kopballen, die vaak videobeginprestaties kunnen verbeteren.

   * Toegevoegde ondersteuning voor het forceren van https-creatieven om op http te worden opgehaald, wat ook de prestaties van het starten van de video kan verbeteren.

* Oplossingen voor beveiliging en onderhoud.

### Versie 20.2.1

**Wanneer:** Donderdag 13 februari 2020, 04.30 tot 05.30 uur Oosterse tijd

* Toegevoegde ondersteuning voor stitching en assets die meerdere alleen-audio streams bevatten op basis van taal/codec/bitsnelheid.
* Kleine prestatieverbeteringen en onderhoudsupdates.

### Versie 20.1.3

**Wanneer:** Dinsdag 28 januari 2020, 23.00 tot 3.00 uur Oosterse tijd

* **VMAP met FER-ondersteuning voor nbc CueFormat**

   Zet cues van FER-stream om in FW-tijdlijnoverschrijvingsparams, wanneer deze `ptcueformat=nbc` wordt gebruikt en de stream een VOD-stream is met aanwijzingen in het manifest en kant-en-klare advertenties.

* Maak user-agent gebied in de Kopbal van HTTP alvorens aan derdeleveranciers/CDN door:sturen.

* Filter controle-/niet-afdrukbare tekens (ASCII-code &lt; 32) uit HTTP-headers van de user-agent voordat u deze verzendt naar Auditude en andere add-providers, CDN&#39;s. Auditude Ad-Call gebruikt om voor dergelijke ongeldige kopballen te ontbreken.

* Verwijder oude V1-objecten van NetStorage-groepen om het aantal objecten binnen de veilige grenzen van Akamai te houden.

### Versie 20.1.2 [Hotfix]

**Wanneer:** Maandag 20 januari 2020, 20.00 - 03.00 uur Oosterse tijd

* Onderhoudsupdates.

### Versie 20.1.1

**Wanneer:** Woensdag 15 januari 2020, 04.00 - 05.00 uur Oosterse tijd

* De service Creative Repackaging biedt nu sneller en invoegender door misvormde creatieve producten automatisch op de zwarte lijst te zetten.

* Toegevoegde fase 1 steun voor nieuw SCTE 35 richtsnoerformaat in server-kant en toevoeging.

* Onderhoudsupgrades.

## Opgeloste problemen

Wanneer de oplossing aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond. Bijvoorbeeld ZD#xxxxx.

**PTAI 20.5.1**

* Problemen met CORS-koppen bij if-Modified-Since-koppen worden verzonden.

* Problemen in het CRS-dashboard.

**PTAI 20.3.4**

* Probleem dat ertoe leidde dat ondertitels niet meer gesynchroniseerd waren na toevoeging van de advertentie in VOD/WebVTT.

**PTAI 20.3.3**

* Probleem met X-Forwarded-For kopballen, waar IPv6 adressen niet correct URL gecodeerd wanneer overgegaan tot de advertentieservers waren.

* Probleem met CMAF/gedemuxed audiostromen, waar in bepaalde scenario&#39;s de aantallen EXT-X-MEDIA-REEKS in bepaalde scenario&#39;s verkeerd stijgen

## Bekende problemen en beperkingen

**PTAI 20.3.3**

Geen nieuwe beperking toegevoegd.
