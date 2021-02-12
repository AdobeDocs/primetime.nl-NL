---
description: De manifestserver coördineert de systemen die inhoud verstrekken, advertenties verstrekken, video spelen, en spooradvertenties. Het ontvangt met M3U8 gecodeerde afspeellijsten (manifests) die door client-videospelers van contentproviders worden ontvangen, advertenties van advertentieleveranciers in de manifests steekt en de vernaakte manifests aan videospelers doorgeeft. De functie ondersteunt zowel client-side als server-side en tracking. Het voert zijn interactie uit gebruikend een op HTTP-Gebaseerde Webdienstinterface.
seo-description: De manifestserver coördineert de systemen die inhoud verstrekken, advertenties verstrekken, video spelen, en spooradvertenties. Het ontvangt met M3U8 gecodeerde afspeellijsten (manifests) die door client-videospelers van contentproviders worden ontvangen, advertenties van advertentieleveranciers in de manifests steekt en de vernaakte manifests aan videospelers doorgeeft. De functie ondersteunt zowel client-side als server-side en tracking. Het voert zijn interactie uit gebruikend een op HTTP-Gebaseerde Webdienstinterface.
seo-title: Overzicht van Manifest Server-interacties
title: Overzicht van Manifest Server-interacties
uuid: 3e314a45-a4dd-492f-8915-19224a8fbbc7
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---


# Overzicht van Manifest Server-interacties {#overview-of-manifest-server-interactions}

De manifestserver coördineert de systemen die inhoud verstrekken, advertenties verstrekken, video spelen, en spooradvertenties. Het ontvangt met M3U8 gecodeerde afspeellijsten (manifests) die door client-videospelers van contentproviders worden ontvangen, advertenties van advertentieleveranciers in de manifests steekt en de vernaakte manifests aan videospelers doorgeeft. De functie ondersteunt zowel client-side als server-side en tracking. Het voert zijn interactie uit gebruikend een op HTTP-Gebaseerde Webdienstinterface.

Een typische configuratie bevat:

* De Primetime-manifestserver
* De Primetime Creative Repackaging Service (CRS)
* Een client, een videospeler besturen
* Een uitgever, gewoonlijk met een Systeem van het Beheer van de Inhoud (CMS)
* Een netwerk voor het leveren van inhoud (CDN)
* Een advertentieserver
* Een ontvanger voor rapporten voor het bijhouden van advertenties

De workflow varieert op basis van een aantal factoren, zoals of de CDN Akamai is of dat de client een advertentie bijhoudt. Voor een diagram van het werkschema voor client-side en tracking, zie [Client-side tracking workflow](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md#section_cst_flow).

De manifeste server communiceert met video-levering cliënten door ontvangen van en het antwoorden op de verzoeken van de GET van HTTP. De reacties zijn in M3U8 gecodeerde manifests die inhoud met advertenties beschrijven, eventueel inclusief een JSON- of VMAP-structuur (sidecar) met gedetailleerde instructies voor het bijhouden van advertenties (zie [Bestandsindelingen](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)).

Een typisch werkschema kijkt als het volgende:

1. De uitgever verzendt de inhoud-URL en de informatie voor de advertentieserver naar de client.
1. De client gebruikt de informatie van de uitgever om een manifestserver-URL te genereren en verzendt een verzoek van de GET naar die URL. Dit wordt de URL van de Bootstrap genoemd.
1. De manifestserver vestigt een zitting met de cliënt.
1. De manifestserver verkrijgt inhoudsmanifests van CDN, die informatie kan omvatten ad onderbreking.
1. De manifestserver richt de cliënt aan master/variant manifest het voor de cliënt opnieuw wordt geproduceerd.

   >[!NOTE]
   >
   >Als de Bootstrap URL vraagparameters `pttrackingmode=simple` of `ptplayer=ios-mobileweb` plaatsen bevat, keert de manifestserver master/variant manifest URL in een voorwerp JSON terug, en de cliënt verzendt een GET verzoek naar dat variant manifest URL.

1. De client kiest een stream in het gegenereerde variantmanifest om af te spelen, te verzenden en informatie naar de manifestserver te verzenden.
1. De manifestserver geeft de door de client opgegeven informatie door aan de advertentieserver en ontvangt advertenties en URL&#39;s voor het bijhouden van advertenties van de advertentieserver. Als een geleverde advertentie niet in formaat HLS is, verzendt de manifestserver het naar CRS voor omzetting in HLS.
1. De manifeste server stitches in content manifest en verzendt het nieuwe vastgemaakte manifest naar de client.
1. De client speelt de inhoud af met de ingesloten advertenties en vraagt op de opgegeven tijdstippen om de opgegeven URL&#39;s voor bijhouden.

Primetime en invoeging ondersteunen clients op veel platforms voor het afspelen van video. Niet alle clients zijn gebaseerd op het Primetime TVSDK-pakket, maar alle clients verzenden GET-aanvragen naar dezelfde basis-URL. De parameters van de vraag onderscheiden één cliëntverzoek van een andere door de manifestserver te vertellen:

* welke cliënt het verzoek indient;
* wat de klant wil,
* en welke informatie voor het bijhouden van advertenties moet worden verstrekt.

## CORS {#section_BEA7F298660944BE92801E4C82FCD038}

De manifestserver gebruikt de norm het Delen van het Middel van de Cross-Origin (CORS). Het zoekt naar een `Origin` kopbal in de verzoeken het ontvangt. Als de koptekst aanwezig is, reageert deze met

* `Access-Control-Allow-Origin: *`tekenreeks uit de koptekst Oorsprong`*`
* `Access-Control-Allow-Credentials: true`
* `Access-Control-Allow-Methods: GET`

Zo nee, dan antwoordt zij met:

* `Access-Control-Allow-Origin: *`
* `Access-Control-Allow-Methods: GET`