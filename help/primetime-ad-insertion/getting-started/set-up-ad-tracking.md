---
title: Advertentie bijhouden instellen
description: Advertentie bijhouden instellen
exl-id: b5ebad0f-4e20-456a-892d-4c981ab26e51
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Advertentie bijhouden instellen {#ser-up-ad-tracking}

De meeste adverteerders hebben informatie nodig over wanneer, hoe lang en hoe goed hun advertenties zijn bekeken. Primetime Ad Insertion ondersteunt client-side, server-side en hybride advertentietracering om deze informatie op flexibele wijze te verzamelen.

## Client Advertentie bijhouden met VMAP/JSON {#client-side-ad-tracking-vmap-json}

In client-side advertentie-tracking verzendt de server de client een JSON-, VMAP- of in-manifest-structuur die gebeurtenissen tracking en URL&#39;s opgeeft, samen met de playlist met advertenties.

Als u het bijhouden van advertenties op de client wilt inschakelen, geeft u de volgende parameters op in het dialoogvenster [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

* `pttrackingmode=simple`

* `pttrackingversion={format version (vmap,v1,v2,v3)}`

>[!NOTE]
>
>De instelling `pttrackingmode=simple` zorgt ervoor dat de eerste API-bootstrap-aanvraag een JSON-reactie retourneert in plaats van een HLS- of DASH-document.

<!-- **Daniel to check. The specified file in this statement does not exist.** 
More information about `pttrackingmode`, `pttrackingversion` formats, can be found in [API Reference: Manifest server query parameters](manifest-server-query-parameters.md). -->

<!--Show examples of how to request a sidecar] -->

## Ad-tracking op de server {#server-side-ad-tracking}

Met deze methode worden gegevens voor het bijhouden van gegevens volledig berekend aan de serverzijde. Dit is handig wanneer het bijwerken van de clienttoepassing niet mogelijk is. Nochtans, kunnen de server-kant en het volgen niet met cliënt-zijplaybackactiviteit aanpassen. De server beschouwt bijvoorbeeld een advertentie die moet worden afgespeeld nadat de segmenten zijn geleverd, zelfs als de eindgebruiker de volledige advertentie niet weergeeft.

Als u gegevensspatiëring op de server wilt inschakelen, geeft u de volgende parameter op in het dialoogvenster [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

`pttrackingmode=sstm`

Zie `pttrackingmode` secties [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).

Alle beacons voor het bijhouden van advertenties worden verzonden met de volgende HTTP-aanvraagheaders:

* `X-Forwarded-For`
* `User-Agent`
* `X-Device-User-Agent`

Deze waarden bevatten het client/player user-agent en client IP-adres.

## Hybride advertentie bijhouden {#hybrid-ad-tracking}

Deze aanpak lijkt op het bijhouden van de server, maar de clienttoepassing vraagt ook om secundaire gegevens van Primetime Ad Insertion voor gedetailleerde traceringsinformatie. Hybride en het volgen kunnen niet-lineaire advertenties zoals overlays en metgezellen aan de cliënttoepassing leveren, terwijl nog het verlaten van Primetime Ad Insertion om individuele en volgende URLs te verzenden.
Als u hybride advertentietracering wilt inschakelen, raadpleegt u de `pttrackingmode` in de [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md).
