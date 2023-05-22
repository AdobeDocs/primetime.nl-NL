---
title: Query-parameters van de server manipuleren
description: De parameters van de vraag vertellen de manifestserver welke soort cliënt het verzoek verzond en wat die cliënt de manifestserver wil doen. Sommige zijn vereist en sommige hebben specifieke acceptabele indelingen of waarden.
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---


# Query-parameters van de server manipuleren {#ms-query-params}

De parameters van de vraag vertellen de manifestserver welke soort cliënt het verzoek verzond en wat die cliënt de manifestserver wil doen. Sommige zijn vereist en sommige hebben specifieke acceptabele indelingen of waarden.

De volledige URL bestaat uit de basis-URL gevolgd door een vraagteken, en vervolgens `parameterName=value` argumenten, gescheiden door ampersands: `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

## Erkende parameters {#section_072845B7FA94468C8068E9092983C9E6}

De manifestserver herkent de volgende parameters. Deze worden samen met alle niet-herkende parameters verwerkt of doorgegeven aan de advertentieserver.

| Sleutel | Beschrijving | Vereist | Geldige waarden |
|---|---|---|---|
| `__sid__` | De unieke id die de manifestserver gebruikt om de sessie-id te genereren. | Ja | Alphanumeric |
| g | Type clientapparaat | Wanneer het richten van regels afhangt van apparatentype | Zie lijst op [Clienttypen](https://adobeprimetime.zendesk.com). Vereist toegang van Zendesk. |
| k | Trefwoorden voor aangepaste advertenties | Nee | URL-veilige tekenreeks in indeling `key1=value1;key2=value2;. . .` |
| u | ID van primetime en invoegmiddel. | Ja | MD5 Hash-waarde |
| z | Id van primetime en invoegzone voor het element. | Ja | Geheel |
| enableC3 | De client bevindt zich in een C3-venster. Indien waar (true), alleen lokale vermeldingen vervangen; anders vervangt u alle beschikbare gegevens. | Nee | Boolean |
| leven | Geeft aan of de inhoud een live stream of een VOD-stream (video on-demand) is. | Akamai Ad Scaler- of iOS Safari-client. | Boolean |
| `pabimode` | [Gedeeltelijke invoeging en onderbreking inschakelen](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/partial-ad-break-insetion.md) ondersteuning. <br> Inschakelen indien waar of begin.<br> Uitschakelen indien onwaar. | Nee (standaard is uitgeschakeld) | start, true of false |
| `ptadwindow` | Duur (seconden) van het venster voor het stikken van objecten: hoe ver terug om te zoeken naar advertenties wanneer een DVR - gebruiker zich bij de stroom aansluit. | Nee (standaard = 1800) | 0 tot en met 1800 |
| `ptassetid` | De unieke id van de inhoud die door de uitgever wordt toegewezen en onderhouden. | Akamai Ad Scaler | URL-veilige tekenreeks |
| `ptcdn` | Lijst van één of meerdere CDNs aan gastheer transcoded activa. Zie [Ondersteuning voor meerdere CDN&#39;s](/help/primetime-ad-insertion/~old-creative-repackaging-service/multi-cdn-supportt.md). | Geen (standaard=Akamai) | Voorbeeld: Akamai, Level3, Limelight, Comcast |
| `ptcueformat` | De naam van de aangepaste ad-cueformaat in de M3U8. | Nee | DPISimple, DPIScte35, Element,NBC, NFL of Turner |
| `ptfailover` | Signaleert de manifestserver om primaire en failover stromen te identificeren die in master playlist worden gespecificeerd, en hen te behandelen als gescheiden reeksen. Dit vergemakkelijkt failover en voorkomt timingsfouten. (Alleen voor Apple HLS-apparaten). Zie  [Omschakelen van HLS-speler vergemakkelijken](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/hls-switching-to-failover.md). | Nee | true |
| `ptmulticall` | Indien ingesteld op true, worden meerdere controles ad-call voor FER uitgevoerd; één voor elke advertentie-onderbreking. Indien afwezig of geplaatst aan vals, wordt één ad-call gemaakt om voor FER te controleren. | Nee | Boolean <br> **Opmerking**: De volgende eisen: <ul><li>`ptcueformat` parameter moet op nbc worden ingesteld</li><li>parameter pttimeline wordt genegeerd.</li></ul> |
| `ptplayer` | Speler die het verzoek indient. | iOS/Safari | ios-mobileweb |
| `ptrendition` | Automatisch gegenereerd door invoeging in een advertentie en gebruikt door Akamai. Toevoegen of verwijderen niet uitvoeren. | Akamai Ad Scaler |  |
| `pttagds` | Inschakelen [EXT-X-DISCONTINUITY-REEKS](https://tools.ietf.org/html/draft-pantos-http-live-streaming-19#section-4.3.3.3) tags | Nee | true - manifestserver bevat een volgnummer vóór de inhoud in elk m3u8-bestand dat het verzendt; als parameter niet aanwezig of niet waar is, neemt de manifestserver geen opeenvolgingstag op. |
| `pttimeline` | Een tekenreeks met de gewenste tijdlijn voor plaatsing en inhoud van de advertentie, die de inhoudsstroom overschrijft en afbreekt. | Nee | [VOD-tijdlijn](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md) |
| `pttoken` | Schakel TS-segmentautorisatietokens in.<br> **Opmerking**: Alleen ondersteunde Akamai CDN-tokens | Voor TS-segmentautorisatietokens | Boolean |
| `pttrackingmode` | Enable ad tracking; ofwel aangepaste client-side (eenvoudig), server-side (sstm) of hybride (eenvoudigst). | Nee | eenvoudig, sstm, of eenvoudig.<br> **Opmerking**: Als deze parameter niet inbegrepen is, wordt #EX-X-MARKER geïnjecteerd in manifest. Zie [EXT-X-MARKERINGSrichtlijn](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/ms-api-playlists.md). |
| `pttrackingposition` | Instrueert de manifestserver om slechts informatie terug te keren en te volgen. Geef deze parameter niet op in de bootstrap-aanvraag. | Client-side tracking | Alfanumerieke notitie: De manifestserver negeert alle overgegaane waarden. Als u echter een null- of lege tekenreeks doorgeeft, retourneert de manifestserver de M3U8 in plaats van informatie te volgen. |
| `pttrackingversion` | De indelingsversie van de traceerinformatie aan de clientzijde. | Client-side tracking | v1, v2, v3 of vmap |
| `scteTracking` | Fetch M3U8, before SCTE tracking information can be fetched in JSON V2 sidecar. <br>Deze parameter geeft aan de manifestserver door dat de speler die de M3U8 haalt, SCTE-taginformatie moet ophalen. | Nee (standaard: false) | true of false. <br> **Opmerking**: De SCTE-35 gegevens zijn teruggekeerd in JSON sidecar met de volgende combinatie waarden van de vraagparameter: <ul><li>`ptcueformat=turner | elemental | nfl | DPIScte35`</li><li>`pttrackingversion=v2`</li><li>`scteTracking=true`</li></ul> |
| `vetargetmultiplier` | Het aantal segmenten vanaf het live punt De pre-roll compensatie wordt gevormd gebruikend: `(vetargetmultiplier * targetduration + vebufferlength`<br/><br/>**Opmerking**: Alleen actief/lineair | Nee (standaard: 3,0) | Float |
| `vebufferLength` | Het aantal seconden vanaf het actieve punt. **Opmerking**: Alleen live/lineair. | Nee (standaard: 3,0) | Float |
