---
title: Opmerkingen bij de release PTAI 20.9.1
description: In de opmerkingen bij de release PTAI 20.9.1 wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in Primetime Dynamic Ad Insertion in 2020.
translation-type: tm+mt
source-git-commit: c23b052f14c6673d4ba2aae6a317a55a2e611e8a
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---


# Opmerkingen bij de release Primetime Dynamic Ad Insertion 20.9.1

Dynamische Ad Insertion 20.9.1-releaseopmerkingen beschrijven wat nieuw of gewijzigd is, problemen die zijn opgelost en bekende problemen in Primetime Dynamic Ad Insertion in 2020.

## Nieuwe functies in PTAI 20.9.1

**Wanneer:** Dinsdag 1 september 2020, 15.30 tot 19.30 uur Oosterse tijd

**Oplossingen**

* Probleem opgelost voor klanten die HLS/CMAF gebruiken, waarbij EXT-X-MAP soms CDN-tokens of EXT-X-MAP-tags niet correct uit het DVR-venster kon worden ingevoerd.

### Verbeteringen en correcties in vorige releaseversies

#### Versie 20.8.4

**Wanneer:** Woensdag 19 augustus 2020, 03.30 - 07.30 uur Oosterse tijd

**Verbeteringen en correcties**

Onderhoudsupdates.

#### Versie 20.8.1

**Wanneer:** Dinsdag 4 augustus 2020, 15.00 tot 18.00 uur Oosterse tijd

**Verbeteringen en correcties**

Onderhoudsupdates.

#### Versie 20.7.1

**Wanneer:** Donderdag 9 juli 2020, 03.00 - 05.00 uur Oosterse tijd

**Nieuwe functies en verbeteringen**

* SCTE35 verhoging om één van beiden van de Bericht van het Begin/van het Eind van de Leverancier te gebruiken of de berichten van het Begin/van het Eind van de Onderbreking om het richtsnoer te identificeren.

* Bijgewerkte X-ADBE-AI-X1 kopbal met extra informatie om het oplossen van problemen te helpen.

* Verbeterde metrische aggregatie.

* Verbeterd SSAI-consoledashboard voor het deelvenster Sessiestatistieken

#### Versie 20.6.2

**Wanneer:** Donderdag 18 juni 2020, 03.00 - 04.00 uur Oosterse tijd

**Verbeteringen**

Verbeterde streamsynchronisatie voor videoclips die precisie in milliseconden vereisen. Neem contact op met de Adobe-ondersteuning om millisecondenprecisie in te schakelen voor `#EXT-X-PROGRAM-DATE-TIME tags`.

#### Versie 20.6.1

**Wanneer:** Dinsdag 2 juni 2020, 03.00 - 05.00 uur Oosterse tijd

**Nieuwe functies**

Neem contact op met de ondersteuning van Adobe om de volgende nieuwe functies in te schakelen via de serverconfiguratie:

* Manifest Manipulation: HLS-segment en bron-URL&#39;s kunnen nu worden getransformeerd tussen HTTP en HTTPS om de prestaties te verbeteren door TLS-handtekeningen op back-end verzoeken te verminderen. Het kan ook worden gebruikt om fragmenten van advertentie/inhoud te verenigen op dezelfde CDN&#39;s.

* VOD in lange vorm: Verbeterde API&#39;s om sessies in leven te houden met VOD-middelen van lange formulieren.

**Bugfixes**

* Probleem verholpen waarbij WebVTT-fragmenten altijd werden aangevraagd onder http-protocol, ongeacht het oorspronkelijke aangevraagde protocol.

* Probleem verholpen waarbij EXT-X-DISCONTINUITY-tags van de bovenkant van de afspeellijst werden verwijderd bij het terugschakelen van advertenties naar inhoud. Neem contact op met de Adobe-ondersteuning om deze oplossing in te schakelen.

#### Versie 20.5.1

**Wanneer:** Dinsdag 5 mei 2020, 04.00 - 05.00 uur Oosterse tijd

* Probleem verholpen om ervoor te zorgen dat correcte kopballen CORS worden verstrekt wanneer if-Modified-Since kopballen worden verzonden.

* Bugfixes op het CRS-dashboard.

* Onderhoudsupdates.

#### Versie 20.3.4

**Wanneer:** Woensdag 1 april 2020, 03.00 - 04.00 uur Oosterse tijd

* Probleem verholpen waarbij ondertitels niet meer gesynchroniseerd werden na het plaatsen van de advertentie in VOD/WebVTT.

* Beveiligingsupdates.

#### Versie 20.3.3

**Wanneer:** Donderdag 26 maart 2020, 03.00 - 04.00 uur Oosterse tijd

* SSAI 4XX en 5XX antwoorden verstrekken nu correct CORS-verwante kopballen, die dwars-domein javascript webview cliënten toestaan om foutenreacties met succes te lezen.

* Probleem verholpen met X-Forwarded-For headers, waarbij IPv6-adressen niet correct URL-gecodeerd waren wanneer ze aan de advertentieservers werden doorgegeven.

* Probleem verholpen met CMAF/gedemuxed audiostreams, waarbij in bepaalde scenario&#39;s de EXT-X-MEDIA-SEQUENTIE-nummers onjuist zouden stijgen.

#### Versie 20.3.2

**Wanneer:** Woensdag 11 maart 2020, 05.30 - 07.00 uur Oosterse tijd

* Verbeteringen aan SCTE35 signaalbehandeling.

* Onderhoudsupdates.

#### Versie 20.3.1

**Wanneer:** Donderdag 5 maart 2020, 20.30 uur tot 04.30 uur Oosterse tijd

* Prestatieverbeteringen:

   * Extra cacheondersteuning voor zowel master manifests als media m3u8. Deze manifests antwoorden nu aan geheime voorgeheugen-controle: de openbare en Max-Leeftijd kopballen, die vaak videobeginprestaties kunnen verbeteren.

   * Toegevoegde ondersteuning voor het forceren van https-creatieven om op http te worden opgehaald, wat ook de prestaties van het starten van de video kan verbeteren.

* Oplossingen voor beveiliging en onderhoud.

#### Versie 20.2.1

**Wanneer:** Donderdag 13 februari 2020, 04.30 tot 05.30 uur Oosterse tijd

* Toegevoegde ondersteuning voor stitching en assets die meerdere alleen-audio streams bevatten op basis van taal/codec/bitsnelheid.
* Kleine prestatieverbeteringen en onderhoudsupdates.

#### Versie 20.1.3

**Wanneer:** Dinsdag 28 januari 2020, 23.00 tot 3.00 uur Oosterse tijd

* **VMAP met FER-ondersteuning voor nbc CueFormat**

   Zet cues van FER-stream om in FW-tijdlijnoverschrijvingsparams, wanneer deze `ptcueformat=nbc` wordt gebruikt en de stream een VOD-stream is met aanwijzingen in het manifest en kant-en-klare advertenties.

* Maak user-agent gebied in de Kopbal van HTTP alvorens aan derdeleveranciers/CDN door:sturen.

* Filter controle-/niet-afdrukbare tekens (ASCII-code &lt; 32) uit HTTP-headers van de user-agent voordat u deze verzendt naar Auditude en andere add-providers, CDN&#39;s. Auditude Ad-Call gebruikt om voor dergelijke ongeldige kopballen te ontbreken.

* Verwijder oude V1-objecten van NetStorage-groepen om het aantal objecten binnen de veilige grenzen van Akamai te houden.

#### Versie 20.1.2 (hotfix)

**Wanneer:** Maandag 20 januari 2020, 20.00 - 03.00 uur Oosterse tijd

* Onderhoudsupdates.

#### Versie 20.1.1

**Wanneer:** Woensdag 15 januari 2020, 04.00 - 05.00 uur Oosterse tijd

* De service Creative Repackaging biedt nu snellere toevoegingen door het automatisch blokkeren van lijsten met misvormde creatieve producten.

* Toegevoegde fase 1 steun voor nieuw SCTE 35 richtsnoerformaat in server-kant en toevoeging.

* Onderhoudsupgrades.

## Opgeloste problemen

Wanneer de oplossing aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond. Bijvoorbeeld: `ZD#xxxxx`

**PTAI 20.6.1**

* `WebVTT` fragmenten werden altijd aangevraagd onder het http-protocol, ongeacht het oorspronkelijke aangevraagde protocol.

* `EXT-X-DISCONTINUITY` -tags worden boven aan de afspeellijst verwijderd wanneer u terugschakelt van advertenties naar inhoud. Neem contact op met de Adobe-ondersteuning om deze oplossing in te schakelen.

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
