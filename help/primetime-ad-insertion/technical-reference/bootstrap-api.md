---
title: Bootstrap API
description: 'Bootstrap API '
translation-type: tm+mt
source-git-commit: bf99c76bbbb67560adc675cf84297b8d3b04e19d
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---


# Bootstrap-API {#bootstrap-api}

De Bootstrap-API is doorgaans de URL die naar de client/video-afspeelAPI&#39;s wordt verzonden.  Voor opties en parameters die kunnen worden gevormd, verwijs naar [Bootstrap API parameters](#bootstrap-api-parameters).

## Een opdracht naar de manifest-server verzenden {#send-a-command-to-the-manifest-server}

1. Verzend een `HTTP GET` verzoek om een laarzentrekker URL die met het volgende patroon wordt samengesteld:

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]
    ?{query parameters}
   ```

   * **File** extensionDefined. `.m3u8` als doelmanifest HLS is,  `.mpd` als doelmanifests in DASH zijn.

   * **** PublisherAssetIDR vereist. De unieke id van de uitgever voor de specifieke inhoud.

   * **Inhoud** URLRequired. URL van de inhoud van het M3U8-bestand, Base64-gecodeerd om veilig te zijn binnen de URL van de manifestserver. De inhoud-URL moet verwijzen naar een M3U8-bestand van een andere type, zelfs als er slechts één bitsnelheidstream is.

   * **De** parameters van de vraagDeze vormen het meest gevarieerde deel van het verzoek. Zij vertellen de duidelijke server welke soort cliënt het verzoek doet en wat het de manifestserver wil doen.

   Bijvoorbeeld:

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTP- vs. HTTPS-aanvragen**

   De manifestserver leidt tot URLs gebruikend het zelfde protocol van HTTP van het verzoek van de cliënt. Wanneer een speler een niet-beveiligd HTTP-verzoek (http) indient, retourneert de manifestserver manifest-URL&#39;s en URL&#39;s voor bijhouden van bestandsgrootte met het http-protocol. Als een speler een beveiligde HTTP-verbinding (https) maakt, geeft de manifestserver duidelijke URL&#39;s en URL&#39;s van Auditude tracking met het https-protocol.

   >[!NOTE]
   >
   >De manifestserver kan het protocol (HTTP of HTTPS) van derde partij het volgen beacons niet veranderen. U moet contact opnemen met de inhoud en externe advertentieproviders om ervoor te zorgen dat deze de gewenste protocollen configureren.  De segmenten URL protocollen kunnen worden veranderd, echter, door gebrek, gebruik de zelfde protocollen die in doelmanifests worden bepaald.

## Bootstrap API-parameters {#bootstrap-api-parameters}

De parameters van de vraag vertellen de manifestserver welke soort cliënt het verzoek verzond en wat die cliënt de manifestserver wil doen. Sommige zijn vereist en sommige hebben specifieke acceptabele indelingen of waarden.
De volledige URL bestaat uit de basis-URL gevolgd door een vraagteken en vervolgens `parameterName=value` argumenten gescheiden door ampersands. Bijvoorbeeld, `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

De manifestserver herkent de volgende parameters. Alle querystring\
parameters worden doorgegeven aan de advertentieserver.

| parameter | beschrijving | formaten |
|---|---|---|
| _zand_ | Een unieke id die de manifestserver zal gebruiken om zitting-id te produceren. | Vereist voor zowel DASH/HLS |
| leven | Hiermee wordt Primetime-Ad Insertion gewaarschuwd dat het doorgegeven inhoudsitem een live stream is.  Als deze parameter niet wordt overgegaan, zal de toevoeging van Primetime en een secundair verzoek op de aanvankelijke duidelijke vraag indienen om te bepalen als manifest of ongeldig is.<br>Mogelijke waarden:<br>true voor live-<br>inhoud false voor vod-<br>inhoud voor automatische detectie | Optioneel voor HLS.  Vereist voor DASH |
| z | De zone-id voor het element dat aan Primetime Ad Insertion moet worden geleverd. Wordt geleverd door uw Adobe Technical Account Manager. | Vereist voor zowel DASH/HLS |
| pabimode | Hiermee schakelt u [gedeeltelijke invoeging en eindinvoeging](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md#partial-ad-break-support) voor live streams in.<br>Mogelijke waarden:<br>true om uit <br>te schakelen (standaard uitgeschakeld) | HLS/DASH |
| ptadtimeout | Hiermee wordt de totale tijd van de advertentie beperkt als downstreamproviders te lang duren om te reageren.  Langdurige reacties kunnen problemen met afspelen veroorzaken. Hierdoor kan Primetime DAI binnen een bepaalde tijdslimiet een reactie afdwingen.<br>Mogelijke waarden:<br>numerieke tekenreeks in milliseconden.<br>Weglaten om uit te schakelen (standaard uitgeschakeld) | HLS/DASH |
| ptadwindow | Duur (in seconden) van het terugzoek- en beslissingsvenster — hoe ver de Ad Insertion van Primetime terug naar ad-cues zoekt wanneer een DVR-gebruiker zich bij de stream aanmeldt. Een waarde van nul zal middenrol en besluitvorming in aanvankelijke manifest onbruikbaar maken, met besluit die slechts na de eerste update hervat. Deze parameter is nuttig om het toevoegen van toevoegingen aan zittingen onbruikbaar te maken die slechts een paar seconden kunnen duren (alias kanaalomdraaiend).<br>Mogelijke waarden:<br>numerieke tekenreeks 0-1800 (standaard 1800) | Alleen HLS |
| ptassetid | De unieke id van de inhoud die door de uitgever wordt toegewezen en onderhouden.  Vereist in combinatie met de Akamai Ad Scaler. | HLS/DASH |
| ptcdn | Lijst van één of meerdere CDNs aan gastheer transcoded activa. Zie [Aflevering en opslag](/help/primetime-ad-insertion/just-in-time-transcoding/delivery-and-storage.md) voor meer informatie.<br>Mogelijke waarden:<br>akamai, niveau3, llnw (lichtnetwerken), comcast.<br>Standaard worden Ad Insertion CDN&#39;s van Primetime gebruikt. | HLS/DASH |
| ptcueformat | De opgegeven indeling van tags die moeten worden uitgevoerd en bepaald (bijvoorbeeld scte35).<br>Mogelijke waarden:<br>dpisimple, dpiscte35, <br>elementalVoor aangepaste actiefindelingen, neemt u contact op met uw technische accountvertegenwoordiger voor de waarde die u voor uw gebruiksgeval wilt gebruiken | HLS/DASH |
| ptfailover | Signaleert de manifestserver om primaire en failover stromen te identificeren die in master playlist worden gespecificeerd, en hen te behandelen als gescheiden reeksen. Dit vergemakkelijkt failover en voorkomt timingsfouten. (Alleen voor Apple HLS-apparaten.) Voor meer informatie, zie [Faciliteren van de speleromschakeling van HLS](hls-switching-to-failover.md) | Alleen HLS |
| ptmulticall | Indien ingeschakeld, wordt een afzonderlijke advertentieaanvraag gedaan voor elke in een VOD-element gevonden bron.  Standaard probeert Primetime Ad Insertion alle beschikbare informatie te verzamelen en deze in één aanvraag naar de advertentieserver te verzenden. Mogelijke waarden:true om in te schakelen, <br>weglaten om uit te schakelen (standaard uitgeschakeld) | HLS/DASH |
| ptparallelstream | Hiermee kunnen klanten met spelers die CMAF-gedemuleerde audio- of videostreams aanvragen, parallel werken om ervoor te zorgen dat advertenties in audio- en videotracks consistent zijn. | Alleen HLS |
| ptprotoswitch | Laat genoemde genoemde manifest het herschrijven regels en ad het halen regels toe, die typisch opstelling door uw technische steunvertegenwoordiger zullen zijn.<br>Voorbeeld: adfetch_fw, cdn_akm | HLS/DASH |
| pttagds | Hiermee wordt injectie van EXT-X-DISCONTINUITY-SEQUENCE-tags in HLS-headers ingeschakeld.Mogelijke waarden:true om uit te schakelen (standaard uitgeschakeld) | Alleen HLS |
| pttimeline | Een tekenreeks met de gewenste tijdlijn voor plaatsing en inhoud van de advertentie, die de inhoudsstroom overschrijft en afbreekt. [ Zie VOD-tijdlijnindeling  ] | HLS/DASH |
| pttoken | Hiermee schakelt u de tokenbeveiligingssystemen voor inhoudsfragmenten/segmenten voor CDN&#39;s<br>Mogelijke waarden in:<br>akamai, llnw (licht), ctl (centurylink) (standaardtokenisatie is uitgeschakeld). | HLS/DASH |
| trackingmodus | Stel rasterschema&#39;s in.<br>Mogelijke waarden:<br>eenvoudig voor client-side en <br>trackingstm voor server-side en <br>trackingsimplesstm voor hybride client/server en tracering (standaard wordt geen advertentie-tracking uitgevoerd) | HLS/DASH |
| trackingpositie | Instrueert de manifestserver om slechts informatie terug te keren en te volgen. Geef deze parameter niet op in de bootstrap-aanvraag.<br>Opmerking: De manifestserver negeert alle overgegaane waarden. Als u echter een null-tekenreeks of een lege tekenreeks doorgeeft, retourneert de manifestserver de M3U8 | HLS/DASH<br>Client-Side Tracking |
| trackingversie | Hiermee stelt u de indelingsversie in die moet worden geretourneerd.<br>Mogelijke waarden:<br>v1, v2, v3 of vmap | HLS/DASH<br>Client-Side Tracking |
| scteTracking | Deze parameter geeft aan de manifestserver door dat de speler die de M3U8 haalt, SCTE-taginformatie moet ophalen.<br>Mogelijke waarden:<br>true of false (standaard false)<br>Opmerking: De SCTE-35 gegevens zijn teruggekeerd in JSON sidecar met de volgende combinatie waarden van de vraagparameter:<br>ptcueformat=turner | elementair | nfl | DPIScte35<br>pttrackingversion=v2<br>scteTracking=true<br> | Alleen HLS |
| vetargetmultiplier | Het aantal segmenten vanaf het live punt De pre-roll compensatie wordt gevormd gebruikend: ( vetargetmultiplier * target duration ) + vebufferlength<br>Opmerking: Deze parameter is alleen van toepassing op Live/Lineaire HLS-streams<br>Mogelijke waarden:<br>Numerieke float<br>(standaard: 3.0 - dezelfde als de HLS-specificatie) | Alleen HLS |
| vebufferLength | Het aantal seconden vanaf het actieve punt dat wordt gebruikt in combinatie met vetargetmultiplier.<br>Opmerking: Deze parameter is van toepassing op Live/Lineaire HLS-streams, <br>alleenMogelijke waarden:<br>numerieke float<br> (standaard: 3,0) | Alleen HLS |
