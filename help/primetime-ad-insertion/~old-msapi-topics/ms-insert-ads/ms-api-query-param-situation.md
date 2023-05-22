---
description: Buiten de basisvraagparameters, laten de facultatieve vraagparameters de duidelijke server toe om met verschillende cliënten en situaties te werken.
title: Optionele queryparameters per client en situatie
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---


# Optionele queryparameters per client en situatie {#optional-query-parameters-by-client-and-situation}

Buiten de basisvraagparameters, laten de facultatieve vraagparameters de duidelijke server toe om met verschillende cliënten en situaties te werken.

## Toevoegen met Akamai Ad Scaler {#section_120FEC75C34D4F4587B77D842166D68A}

Op het Akamai-netwerk voor de levering van inhoud (CDN) werkt de Akamai Edge-server als een intermediair tussen de client en de manifestserver. Als u ook Advertentiescaler gebruikt, `ptassetid` en `live` De vraagparameters verstrekken vereiste informatie aan Akamai Edge.

De `ptassetid` parameter is de id van de uitgever voor zijn element. Akamai gebruikt dit, eerder dan basis64-Gecodeerde URL die u als deel van verzoek URL verstrekt, om playlist te identificeren om aan de manifestserver voor advertentie toevoeging te verstrekken.

De `live` parameter maakt onderscheid tussen live content en video on demand (VOD). De manifestserver heeft deze informatie nodig om zijn gestroomlijnde interface met Akamai te steunen.

Hier volgt een voorbeeld-URL met de parameters die betrekking hebben op Akamai:

```
https://. . .master.m3u8?. . .&ptassetid=pubAsset&live=true
```

## Toevoegen van TVSDK aan Xbox {#section_5DB405F4647240A0B83E72DE35D5EC80}

Een speler die op Primetime TVSDK op Xbox wordt gebaseerd, hoeft geen extra queryparameters te leveren die verder gaan dan de standaardparameters.

## Voeg toe vanaf TVSDK op iOS met Safari {#section_250E493A125E4F82940D19C7DA2AAB2E}

Als een speler op basis van Primetime TVSDK op iOS de Safari-browser gebruikt, moet de `ptplayer` en `live` naast de standaardqueryparameters.

De manifestserver herkent de `ptplayer` value `ios-mobileweb` en verwijdert de pre-rol uit het ad-stitched manifest het terugkeert.

De `live` parameter vertelt de manifestserver of om levende of VOD inhoud terug te keren.

Hier volgt een voorbeeld-URL met de parameters die betrekking hebben op iOS met Safari:

```URL
https://. . .master.m3u8?. . .&ptplayer=ios-mobileweb&live=false
```

## Voeg toevoeging toe gebruikend een douane ad richtsnoerformaat {#section_82AF880AAABE4BD4B593D906434D4D89}

Adobe geeft namen voor advertentievormen die niet rechtstreeks in het Primetime-pakket worden ondersteund. Als u een dergelijke indeling wilt gebruiken, voert u de door de Adobe opgegeven naam in als de waarde van de `ptcueformat` parameter.

Hier volgt een voorbeeld-URL die een aangepaste ad-actiefindeling opgeeft:

```URL
https://. . .master.m3u8?. . .&ptcueformat=[custom format name]
```

## Voeg toevoeging toe met ad-cues om een FreeWheel-tijdlijn voor VOD te maken {#section_E0D830F5EEE24639819B975B90F6999F}

Stel voor VOD-inhoud met ad-cues die moeten worden geparseerd en opgenomen in een FreeWheel-advertentieverzoek de waarde in van de optie `ptcueformat` parameter to `DPIsimple`.

Hier volgt een voorbeeld-URL die het gebruik van een FreeWheel-tijdlijn voor VOD opgeeft:

```URL
https://. . .master.m3u8?. . .&ptcueformat=DPISimple&live=false
```

## Toevoegen met een aangepaste tijdlijn voor VOD {#section_F398F7659164463FA886A4CC787C7B5A}

Als u de manifestserver wilt vragen om advertenties in te voegen in VOD-inhoud volgens een tijdlijn die u opgeeft, stelt u de waarde van de `pttimeline` aan een tekenreeks die de tijdlijn opgeeft. Zie [Tijdlijnindeling VOD](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md).

Hier volgt een voorbeeld-URL die een aangepaste tijdlijn voor VOD gebruikt:

```URL
https://. . .master.m3u8?. . .&live=false&pttimeline=B,60,2,p;C,120,1;B,30,2,m;C,300,1
```

Hiermee wordt een eerste einde van één minuut opgegeven met maximaal twee advertenties, gevolgd door een inhoudssegment van twee minuten, gevolgd door een onderbreking van 30 seconden met maximaal twee advertenties, gevolgd door een inhoudssegment van vijf minuten.

Het stitching voor een chronologie van de douaneinhoud voor VOD inhoud gedraagt zich als volgt:

* De advertentie wordt weergegeven bij de dichtstbijzijnde eindgrens na de tijd die door de advertentieserver is opgegeven.

* Segmenten zijn minstens twee seconden lang.

## TS-segmenten autoriseren {#section_BF855A4399DC42CB8C0586113A416BBC}

Adobe ondersteunt deze functie alleen voor de Akamai CDN. Live HTTP-streaming (HLS) levert transportstreamsegmenten (TS) met behulp van een M3U8-afspeellijst op streamniveau. Er worden meerdere afspeellijsten op streamniveau aan de client aangeboden in een variant van de M3U8-afspeellijst. De client kiest één afspeellijststream in de lijst met varianten en downloadt vervolgens TS-segmenten in die afspeellijst op streamniveau een voor een. In normale verrichting, kan de gevraagde inhoud koekjesvergunning vereisen, die de duidelijke server onzichtbaar op de achtergrond behandelt. Het extraheert het cookie uit de onbewerkte inhoud en voegt een geschikte token toe aan de URL die moet worden gebruikt voor het aanvragen van de geselecteerde stream van de afspeellijst.

Wanneer de Bootstrap URL-queryparameters `pttoken=true`, vereist de uitgever dat een koekje wordt gebruikt in het vragen van elk TS segment, eerder dan slechts één voor de volledige stroom. De manifestserver verbindt dit koekje als vraagparameter aan elk TS segment URL in de stroom playlist het terugstuurt.
