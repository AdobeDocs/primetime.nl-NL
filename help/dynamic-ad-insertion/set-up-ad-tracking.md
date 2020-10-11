---
title: Advertentie bijhouden instellen
description: Advertentie bijhouden instellen
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Advertentie bijhouden instellen {#ser-up-ad-tracking}

De meeste adverteerders hebben informatie nodig over wanneer, hoe lang en hoe goed hun advertenties zijn bekeken. Primetime Ad Insertion ondersteunt client-side, server-side en hybride advertentietracering om deze informatie op flexibele wijze te verzamelen.

## Client Advertentie bijhouden met VMAP/JSON {#client-side-ad-tracking-vmap-json}

In client-side advertentie-tracking verzendt de server de client een JSON-, VMAP- of in-manifest-structuur die gebeurtenissen tracking en URL&#39;s opgeeft, samen met de playlist met advertenties.

Geef de volgende parameters op in de [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)om het bijhouden van advertenties op de client in te schakelen.

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>Door het instellen van de `pttrackingmode=simple` methode wordt de initiële API-aanvraag voor bootstrap gebruikt om een JSON-reactie te retourneren in plaats van een HLS- of DASH-document.

Meer informatie over `pttrackingmode`, `pttrackingversion` indelingen, vindt u in de [API-naslaggids: De parameters](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)van de servervraag van het manifest.

## Ad-tracking op de server {#server-side-ad-tracking}

Met deze methode worden gegevens voor het bijhouden van gegevens volledig berekend aan de serverzijde. Dit is handig wanneer het bijwerken van de clienttoepassing niet mogelijk is. Nochtans, kunnen de server-kant en het volgen niet met cliënt-zijplaybackactiviteit aanpassen. De server beschouwt bijvoorbeeld een advertentie die moet worden afgespeeld nadat de segmenten zijn geleverd, zelfs als de eindgebruiker de volledige advertentie niet weergeeft.

Geef de volgende parameter op in de [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)om het bijhouden van servergegevens in te schakelen.

`pttrackingmode=sstm`

Zie `pttrackingmode` secties van de [Bootstrap API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md).

Alle beacons voor het bijhouden van advertenties worden verzonden met de volgende HTTP-aanvraagheaders:

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

Deze waarden bevatten het client/player user-agent en client IP-adres.

## Hybride advertentie bijhouden {#hybrid-ad-tracking}

Deze aanpak lijkt op het bijhouden van de server, maar de clienttoepassing vraagt ook om secundaire gegevens van Primetime Ad Insertion voor gedetailleerde traceringsinformatie. Hybride en het volgen kunnen niet-lineaire advertenties zoals overlays en metgezellen aan de cliënttoepassing leveren, terwijl nog het verlaten van Primetime Ad Insertion om individuele en volgende URLs te verzenden.
Raadpleeg de `pttrackingmode` parameter in de [Bootstrap-API](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)om hybride en bijgehouden gegevens in te schakelen.
