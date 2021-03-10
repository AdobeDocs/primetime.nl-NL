---
description: Buiten de basisvraagparameters, laten de facultatieve vraagparameters de duidelijke server toe om met verschillende cliënten en situaties te werken.
title: Optionele queryparameters per client en situatie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---


# Optionele queryparameters per client en situatie {#optional-query-parameters-by-client-and-situation}

Buiten de basisvraagparameters, laten de facultatieve vraagparameters de duidelijke server toe om met verschillende cliënten en situaties te werken.

## Toevoegen met Akamai Ad Scaler {#section_120FEC75C34D4F4587B77D842166D68A}

Op het Akamai-netwerk voor de levering van inhoud (CDN) werkt de Akamai Edge-server als een intermediair tussen de client en de manifestserver. Als u ook Ad Scaler gebruikt, geven de query-parameters `ptassetid` en `live` vereiste informatie aan Akamai Edge.

De parameter `ptassetid` is de id van de uitgever voor zijn element. Akamai gebruikt dit, eerder dan basis64-Gecodeerde URL die u als deel van verzoek URL verstrekt, om playlist te identificeren om aan de manifestserver voor advertentie toevoeging te verstrekken.

De parameter `live` maakt onderscheid tussen live-inhoud en video op verzoek (VOD). De manifestserver heeft deze informatie nodig om zijn gestroomlijnde interface met Akamai te steunen.

Hier volgt een voorbeeld-URL met de parameters die betrekking hebben op Akamai:

```
https://. . .master.m3u8?. . .&ptassetid=pubAsset&live=true
```

## Voeg toe van TVSDK op Xbox {#section_5DB405F4647240A0B83E72DE35D5EC80}

Een speler die op Primetime TVSDK op Xbox wordt gebaseerd, hoeft geen extra queryparameters te leveren die verder gaan dan de standaardparameters.

## Voeg toe vanaf TVSDK op iOS met Safari {#section_250E493A125E4F82940D19C7DA2AAB2E}

Een speler op basis van Primetime TVSDK op iOS die de Safari-browser gebruikt, moet naast de standaardqueryparameters ook de parameters `ptplayer` en `live` opgeven.

De manifestserver herkent de `ptplayer` waarde `ios-mobileweb` en elimineert pre-rol van ad-stitched manifest het terugkeert.

De parameter `live` vertelt de manifestserver of om levende of VOD inhoud terug te keren.

Hier volgt een voorbeeld-URL met de parameters die betrekking hebben op iOS met Safari:

```URL
https://. . .master.m3u8?. . .&ptplayer=ios-mobileweb&live=false
```

## Voeg toevoeging toe gebruikend een douane ad richtsnoerformaat {#section_82AF880AAABE4BD4B593D906434D4D89}

Adobe geeft namen voor advertentievormen die niet rechtstreeks in het Primetime-pakket worden ondersteund. Als u een dergelijke indeling wilt gebruiken, geeft u de door Adobe opgegeven naam op als de waarde van de parameter `ptcueformat`.

Hier volgt een voorbeeld-URL die een aangepaste ad-actiefindeling opgeeft:

```URL
https://. . .master.m3u8?. . .&ptcueformat=[custom format name]
```

## Voeg toevoeging toe met ad-cues om een FreeWheel-tijdlijn voor VOD {#section_E0D830F5EEE24639819B975B90F6999F} te maken

Stel de waarde van de parameter `ptcueformat` in op `DPIsimple` voor VOD-inhoud die ad-cues bevat die moeten worden geparseerd en opgenomen in een aanvraag voor een FreeWheel-advertentie.

Hier volgt een voorbeeld-URL die het gebruik van een FreeWheel-tijdlijn voor VOD opgeeft:

```URL
https://. . .master.m3u8?. . .&ptcueformat=DPISimple&live=false
```

## Toevoegen met een aangepaste tijdlijn voor VOD {#section_F398F7659164463FA886A4CC787C7B5A}

Als u de manifestserver wilt vragen om advertenties in te voegen in VOD-inhoud volgens een tijdlijn die u opgeeft, stelt u de waarde van de parameter `pttimeline` in op een tekenreeks die de tijdlijn opgeeft. Zie [Tijdlijnindeling VOD](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md).

Hier volgt een voorbeeld-URL die een aangepaste tijdlijn voor VOD gebruikt:

```URL
https://. . .master.m3u8?. . .&live=false&pttimeline=B,60,2,p;C,120,1;B,30,2,m;C,300,1
```

Hiermee wordt een eerste einde van één minuut opgegeven met maximaal twee advertenties, gevolgd door een inhoudssegment van twee minuten, gevolgd door een onderbreking van 30 seconden met maximaal twee advertenties, gevolgd door een inhoudssegment van vijf minuten.

Het stitching voor een chronologie van de douaneinhoud voor VOD inhoud gedraagt zich als volgt:

* De advertentie wordt weergegeven bij de dichtstbijzijnde eindgrens na de tijd die door de advertentieserver is opgegeven.

* Segmenten zijn minstens twee seconden lang.

## TS-segmenten {#section_BF855A4399DC42CB8C0586113A416BBC} autoriseren

Adobe ondersteunt deze functie alleen voor de Akamai CDN. Live HTTP-streaming (HLS) levert transportstreamsegmenten (TS) met behulp van een M3U8-afspeellijst op streamniveau. Er worden meerdere afspeellijsten op streamniveau aan de client aangeboden in een variant van de M3U8-afspeellijst. De client kiest één afspeellijststream in de lijst met varianten en downloadt vervolgens TS-segmenten in die afspeellijst op streamniveau een voor een. In normale verrichting, kan de gevraagde inhoud koekjesvergunning vereisen, die de duidelijke server onzichtbaar op de achtergrond behandelt. Het extraheert het cookie uit de onbewerkte inhoud en voegt een geschikte token toe aan de URL die moet worden gebruikt voor het aanvragen van de geselecteerde stream van de afspeellijst.

Wanneer de Bootstrap URL vraagparameters `pttoken=true` omvatten, vereist de uitgever een koekje dat in het vragen van elk TS segment wordt gebruikt, eerder dan enkel eens voor de volledige stroom. De manifestserver verbindt dit koekje als vraagparameter aan elk TS segment URL in de stroom playlist het terugstuurt.
