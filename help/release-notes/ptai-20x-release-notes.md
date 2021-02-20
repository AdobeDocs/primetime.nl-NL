---
title: Opmerkingen bij de release PTAI 20.12.1
description: In de PTAI-release wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in Primetime Ad Insertion in 2020.
translation-type: tm+mt
source-git-commit: 8133c35bed7fc72a6c642016a2a4b69204ad8f7a
workflow-type: tm+mt
source-wordcount: '1081'
ht-degree: 0%

---


# Opmerkingen bij de release Primetime Ad Insertion 20.12.1

Opmerkingen bij de release van Primetime Ad Insertion 20.12.1 beschrijven nieuwe of gewijzigde, opgeloste problemen en bekende problemen in Primetime Ad Insertion in 2020.

## Nieuwe functies in PTAI 20.12.1

**Wanneer:** Dinsdag, 08 december, 2020 van 01:00 AM aan 04:00 oosterse Tijd

**Wijzigingen**

* Bevat hotfix om problemen met intermitterende clientconnectiviteit (5xx) te verhelpen in Primetime Ad Insertion die op 30 november 2020 zijn aangetroffen.

## Verbeteringen en correcties in vorige releaseversies

### Versie 20.11.1

**Wanneer:** Donderdag, 5 november 2020 van 2:00 uur tot 05:00 uur Oosterse tijd

**Wijzigingen**

* Onderhoudsupdates.

### Versie 20.10.2

**Wanneer:** Donderdag, 29 okt, 2020 van 12.01 uur tot 06.00 uur Oosterse tijd

**Wijzigingen**

* Onderhoudsupdates.

### Versie 20.10.1

**Wanneer:** Dinsdag, 13 oktober 2020, 03.00 - 07.00 uur Oosterse tijd

**Wijzigingen**

* Onderhoudsupdates.

### Versie 20.9.3

**Wanneer:** Woensdag, 30 september, 2020 om 3:30:00 tot 6:30:00 Oosterse Tijd

**Wijzigingen**

* Toegevoegde Bootstrap API-parameter `ptparallelstream`. Hierdoor kunnen klanten met spelers die CMAF-gedemuleerde audio- of videostreams aanvragen, parallel werken om ervoor te zorgen dat advertenties in audio- en videotracks consistent zijn. Stel de parameterwaarde in op true om deze functie in te schakelen of op weglaten om uit te schakelen.

### Versie 20.9.2

**Wanneer:** Dinsdag, 15 september 2020 van 3:30 uur tot 6:30 uur Oosterse tijd

**Verbeteringen**

* Bied ondersteuning voor het opnemen van niet-lineaire advertentietypen met behulp van `EXT-X-MARKER`-tags.
Neem voor meer informatie of om deze functie in te schakelen contact op met uw medewerker van de technische ondersteuning.

* Bied ondersteuning voor het beperken van de totale tijd voor advertentie-oplossing, als providers te lang duren om te reageren. Om het beperken toe te laten, plaats de laarzentrekker API parameter `ptadtimeout` aan een waarde in milliseconden.

   >[!NOTE]
   >
   >Deze time-out is alleen van toepassing op advertentieverzoeken en niet op creatieve verzoeken.

### Versie 20.9.1

**Wanneer:** Dinsdag, 1 september 2020 van 3:30 tot 7:30 Oost Tijd

**Wijzigingen**

* Probleem opgelost voor klanten die HLS/CMAF gebruiken, waarbij EXT-X-MAP soms CDN-tokens of EXT-X-MAP-tags niet correct uit het DVR-venster kon worden ingevoerd.

### Versie 20.8.4

**Wanneer:** Woensdag, 19 augustus 2020, 03.30 uur tot 07.30 uur Oosterse tijd

**Verbeteringen en correcties**

Onderhoudsupdates.

### Versie 20.8.1

**Wanneer:** Dinsdag, 4 augustus, 2020 van 3.00 uur tot 6.00 uur Oosterse tijd

**Verbeteringen en correcties**

Onderhoudsupdates.

### Versie 20.7.1

**Wanneer:** Donderdag, 9 juli 2020, 03.00 - 05.00 uur Oosterse tijd

**Nieuwe functies en verbeteringen**

* SCTE35 verhoging om één van beiden van de Bericht van het Begin/van het Eind van de Leverancier te gebruiken of de berichten van het Begin/van het Eind van de Onderbreking om het richtsnoer te identificeren.

* Bijgewerkte X-ADBE-AI-X1 kopbal met extra informatie om het oplossen van problemen te helpen.

* Verbeterde metrische aggregatie.

* Verbeterd SSAI-consoledashboard voor het deelvenster Sessiestatistieken

### Versie 20.6.2

**Wanneer:** Donderdag, 18 juni 2020, 03.00 - 04.00 uur Oosterse tijd

**Verbeteringen**

Verbeterde streamsynchronisatie voor videoclips die precisie in milliseconden vereisen. Neem contact op met de Adobe-ondersteuning om millisecondenprecisie in te schakelen voor `#EXT-X-PROGRAM-DATE-TIME tags`.

### Versie 20.6.1

**Wanneer:** Dinsdag, 2 juni, 2020 van 03:00 AM aan 05:00 oosterse Tijd

**Nieuwe functies**

Neem contact op met de ondersteuning van Adobe om de volgende nieuwe functies in te schakelen via de serverconfiguratie:

* Manifest Manipulation: HLS-segment en bron-URL&#39;s kunnen nu worden getransformeerd tussen HTTP en HTTPS om de prestaties te verbeteren door TLS-handtekeningen op back-end verzoeken te verminderen. Het kan ook worden gebruikt om fragmenten van advertentie/inhoud te verenigen op dezelfde CDN&#39;s.

* VOD in lange vorm: Verbeterde API&#39;s om sessies in leven te houden met VOD-middelen van lange formulieren.

**Bugfixes**

* Probleem verholpen waarbij WebVTT-fragmenten altijd werden aangevraagd onder http-protocol, ongeacht het oorspronkelijke aangevraagde protocol.

* Probleem verholpen waarbij EXT-X-DISCONTINUITY-tags van de bovenkant van de afspeellijst werden verwijderd bij het terugschakelen van advertenties naar inhoud. Neem contact op met de Adobe-ondersteuning om deze oplossing in te schakelen.

### Versie 20.5.1

**Wanneer:** Dinsdag, 5 mei 2020 van 04:00 tot 05:00 uur Oosterse tijd

* Probleem verholpen om ervoor te zorgen dat correcte kopballen CORS worden verstrekt wanneer if-Modified-Since kopballen worden verzonden.

* Bugfixes op het CRS-dashboard.

* Onderhoudsupdates.

### Versie 20.3.4

**Wanneer:** Woensdag, 1 april 2020 van 03:00 tot 04:00 Oost Tijd

* Probleem verholpen waarbij ondertitels niet meer gesynchroniseerd werden na het plaatsen van de advertentie in VOD/WebVTT.

* Beveiligingsupdates.

### Versie 20.3.3

**Wanneer:** Donderdag, 26 maart 2020, 03.00 - 04.00 uur Oosterse tijd

* SSAI 4XX en 5XX antwoorden verstrekken nu correct CORS-verwante kopballen, die dwars-domein javascript webview cliënten toestaan om foutenreacties met succes te lezen.

* Probleem verholpen met X-Forwarded-For headers, waarbij IPv6-adressen niet correct URL-gecodeerd waren wanneer ze aan de advertentieservers werden doorgegeven.

* Probleem verholpen met CMAF/gedemuxed audiostreams, waarbij in bepaalde scenario&#39;s de EXT-X-MEDIA-SEQUENTIE-nummers onjuist zouden stijgen.

### Versie 20.3.2

**Wanneer:** Woensdag, 11 maart 2020, 05.30 - 07.00 uur Oosterse tijd

* Verbeteringen aan SCTE35 signaalbehandeling.

* Onderhoudsupdates.

### Versie 20.3.1

**Wanneer:** donderdag, 5 maart, 2020 van 02:30 uur tot 04:30 uur Oosterse tijd

* Prestatieverbeteringen:

   * Extra cacheondersteuning voor zowel master manifests als media m3u8. Deze manifests antwoorden nu aan geheime voorgeheugen-controle: de openbare en Max-Leeftijd kopballen, die vaak videobeginprestaties kunnen verbeteren.

   * Toegevoegde ondersteuning voor het forceren van https-creatieven om op http te worden opgehaald, wat ook de prestaties van het starten van de video kan verbeteren.

* Oplossingen voor beveiliging en onderhoud.

### Versie 20.2.1

**Wanneer:** Donderdag, 13 februari 2020, 04.30 uur tot 05.30 uur Oosterse tijd

* Toegevoegde ondersteuning voor stitching en assets die meerdere alleen-audio streams bevatten op basis van taal/codec/bitsnelheid.
* Kleine prestatieverbeteringen en onderhoudsupdates.

### Versie 20.1.3

**Wanneer:** Dinsdag, 28 januari, 2020 van 2:00 AM aan 03:00 oosterse Tijd

* **VMAP met FER-ondersteuning voor nbc CueFormat**

   Zet cues van FER-stream om in FW-tijdlijnoverschrijvingsparams, wanneer `ptcueformat=nbc` wordt gebruikt en de stream een VOD-stream is met in-manifest aanwijzingen en kant-en-klare advertenties.

* Maak user-agent gebied in de Kopbal van HTTP alvorens aan derdeleveranciers/CDN door:sturen.

* Filter controle-/niet-afdrukbare tekens (ASCII-code &lt; 32) uit HTTP-headers van de user-agent voordat u deze verzendt naar Auditude en andere add-providers, CDN&#39;s. Auditude Ad-Call gebruikt om voor dergelijke ongeldige kopballen te ontbreken.

* Verwijder oude V1-objecten van NetStorage-groepen om het aantal objecten binnen de veilige grenzen van Akamai te houden.

### Versie 20.1.2 (hotfix)

**Wanneer:** Maandag, 20 januari, 2020 van 02:00 AM aan 03:00 Oost Tijd

* Onderhoudsupdates.

### Versie 20.1.1

**Wanneer:** Woensdag, 15 januari 2020 van 04.00 uur tot 05.00 uur Oosterse tijd

* De service Creative Repackaging biedt nu snellere toevoegingen door het automatisch blokkeren van lijsten met misvormde creatieve producten.

* Toegevoegde fase 1 steun voor nieuw SCTE 35 richtsnoerformaat in server-kant en toevoeging.

* Onderhoudsupgrades.

## Opgeloste problemen {#Resolved-issues}

Wanneer de oplossing aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond. Bijvoorbeeld, `ZD#xxxxx`.

**PTAI 20.9.1**

* Probleem opgelost voor klanten die HLS/CMAF gebruiken, waarbij EXT-X-MAP soms CDN-tokens of EXT-X-MAP-tags niet correct uit het DVR-venster kon worden ingevoerd.

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

**PTAI 20.10.1**

Geen nieuwe beperking toegevoegd.