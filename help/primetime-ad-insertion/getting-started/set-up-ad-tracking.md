---
title: Advertentie bijhouden instellen
description: Advertentie bijhouden instellen
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Advertentie-tracking {#ser-up-ad-tracking} instellen

De meeste adverteerders hebben informatie nodig over wanneer, hoe lang en hoe goed hun advertenties zijn bekeken. Primetime Ad Insertion ondersteunt client-side, server-side en hybride advertentietracering om deze informatie op flexibele wijze te verzamelen.

## Client-kant en opvolgen met VMAP/JSON {#client-side-ad-tracking-vmap-json}

In client-side advertentie-tracking verzendt de server de client een JSON-, VMAP- of in-manifest-structuur die gebeurtenissen tracking en URL&#39;s opgeeft, samen met de playlist met advertenties.

Om client-side en tracking in te schakelen, geeft u de volgende parameters op in de [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>Als u `pttrackingmode=simple` instelt, retourneert de initiële API-bootstrap-aanvraag een JSON-reactie in plaats van een HLS- of DASH-document.

<!-- **Daniel to check. The specified file in this statement does not exist.** 
More information about `pttrackingmode`, `pttrackingversion` formats, can be found in [API Reference: Manifest server query parameters](manifest-server-query-parameters.md). -->

<!--Show examples of how to request a sidecar] -->

## Advertentie {#server-side-ad-tracking} op de server bijhouden

Met deze methode worden gegevens voor het bijhouden van gegevens volledig berekend aan de serverzijde. Dit is handig wanneer het bijwerken van de clienttoepassing niet mogelijk is. Nochtans, kunnen de server-kant en het volgen niet met cliënt-zijplaybackactiviteit aanpassen. De server beschouwt bijvoorbeeld een advertentie die moet worden afgespeeld nadat de segmenten zijn geleverd, zelfs als de eindgebruiker de volledige advertentie niet weergeeft.

Om server-kant en het volgen toe te laten, specificeer de volgende parameter in [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

`pttrackingmode=sstm`

Zie `pttrackingmode` secties van [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

Alle beacons voor het bijhouden van advertenties worden verzonden met de volgende HTTP-aanvraagheaders:

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

Deze waarden bevatten het client/player user-agent en client IP-adres.

## Hybride advertentie bijhouden {#hybrid-ad-tracking}

Deze aanpak lijkt op het bijhouden van de server, maar de clienttoepassing vraagt ook om secundaire gegevens van Primetime Ad Insertion voor gedetailleerde traceringsinformatie. Hybride en het volgen kunnen niet-lineaire advertenties zoals overlays en metgezellen aan de cliënttoepassing leveren, terwijl nog het verlaten van Primetime Ad Insertion om individuele en volgende URLs te verzenden.
Raadpleeg de parameter `pttrackingmode` in de [Bootstrap-API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) om hybride advertentie-tracking in te schakelen.