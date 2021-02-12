---
title: Verboden logboekregistratie
description: null
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 0%

---


# Uitgebreide logboekregistratie {#verbose-logging}

## ptdebug-/logboekgebeurtenisbeschrijvingen {#ptdebug-logging-events}

Wanneer het in werking stellen zuivert registreren voor een manifestserverzitting, kunt u de `ptdebug` parameter aan het verzoek URL toevoegen om de volgende opties voor de informatie te specificeren die de manifestserver in de kopballen van HTTP terugkeert:

* `ptdebug=true`
Alle verslagen behalve TRACE_HTTP_HEADER en de meeste vraag/reactiegegevens van TRACE_AD_CALL verslagen.

* `ptdebug=AdCall`
Alleen TRACE_AD_ type (bijvoorbeeld TRACE_AD_CALL) records.

* `ptdebug=Header`
Alleen TRACE_HTTP_HEADER-records.

## Opmaak van logrecords {#log-record-formats}

Elke logrecord heeft een type en een set velden, waarvan sommige optioneel kunnen zijn. De velden van alle records tot het recordtype zijn gelijk. Zij verstrekken een timestamp en informatie over de zitting. Het recordtype identificeert het type gebeurtenis dat wordt geregistreerd, en de verdere gebieden verstrekken informatie over de geregistreerde gebeurtenis.

De structuur van een logrecord is als volgt:

`datetime request_id session_id zone_id record_type other fields`.

| Veld | Type | Beschrijving |
|---|---|---|
| datetime | string | Tijdstempel |
| request_id | string | Verzoek-id gebruikt door de manifestserver (Unix-tijdstempel) |
| session_id | string | Sessie-id gebruikt door de manifestserver |
| zone_id | integer | Zone |
| record_type | string | Type gebeurtenis dat wordt geregistreerd |
| overige velden | variëren | Afhankelijk van het type gebeurtenis |

De verslagen van dit type registreren de resultaten van HTTP- verzoeken. De gebieden voorbij `TRACE_REQUEST_INFO` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| status | string | Geretourneerde HTTP-statuscode |
| request_method | string | HTTP-methode (GET of POST) |
| request_uri | string | HTTP-aanvraagURI (zonder host) |
| request_length | integer | Duur van aanvraag (bytes) |
| response_length | integer | Lengte van reactie (bytes) |
| delta | integer | Tijd (milliseconden) om verzoek te verwerken |
| module_type | string | Variant, stroom of VOD |
| remote_address_aud_client_ip | string | **‡** |
| remote_address_x_fwd_for_hdr_key | string | **‡** |
| remote_host_port | string | **‡** |

**‡** De laatste drie velden zijn optioneel.

**Een voorbeeld**

```shell
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER-records {#trace-http-header-records}

Verslagen van dit type de kopballen van HTTP van het logboek tijdens de vraag van HTTP tussen de manifestserver en cliënt, en server, of inhoudsserver ruilden. De gebieden voorbij TRACE_HTTP_HEADER verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| request_type | string | Type verzoek (MAIN of ONBEKEND) |
| request_response | string | Responsheader (verzoek of antwoord) |
| header_name | string | HTTP-headernaam |
| header_value | string | Base64-gecodeerde HTTP-headerwaarde |

>[!NOTE]
>
>De velden `request_type` en `header_value` zijn optioneel.

**Een voorbeeld**

```shell
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_MISC Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST Cookie aGRu. . .
2015-03-25T06:10:00.928Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST User-Agent TW96aW. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Server bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Content-Type YXBwb. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Last-Modified V2VkL. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE ETag IjIyY2. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Vary QWNjZXB. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Cache-Control bWF4LW. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Expires V2VkL. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Date V2VkLCA. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Age MQ==
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Via MS4xIH. . .
```

### TRACE_AD_CALL records {#tracing-ad-call-records}

De verslagen van dit type registreren de resultaten van manifestserver en verzoeken. De gebieden voorbij `TRACE_AD_CALL` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| status | string | Geretourneerde HTTP-statuscode |
| request_duration | integer | Tijd (milliseconden) van verzoek tot antwoord |
| ad_server_query_url | string | URL voor de advertentievraag, met inbegrip van vraagparameters |
| ad_system_id | string | Systeem toevoegen, van de reactie van de advertentieserver (Auditude indien niet opgegeven) |
| avail_id | string | Id van de zegel, van de advertentie in het contentmanifest-bestand (N.v.t. VOD) |
| avail_duration | getal | Duur (in seconden) van de golf, van de advertentie in het contentmanifest-bestand (N.v.t. VOD) |
| ad_server_response | string | Base64-gecodeerde reactie van een advertentieserver |

Een voorbeeld:

```shell
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT, TRACE_AD_RESOLVE en TRACE_AD_REDIRECT records {#trace-ad-insert-resolve-redirect}

De verslagen van dit type registreren de resultaten van de ad verzoeken die door het verslagtype worden vermeld. Velden buiten het recordtype worden weergegeven in de volgorde die in de tabel wordt weergegeven, gescheiden door tabs.

| Veld | Type | Beschrijving |
|---|---|---|
| status | string | Geretourneerde HTTP-statuscode. |
| avail_id | string | Id van de licentie, van de advertentie in het manifestbestand voor de inhoud (live) of van de manifestserver (VOD). |
| ad_type | string | Type advertentie (DIRECT of REDIRECT). |
| ad_duration | integer | Duur (seconden) van advertentie, van reactie van de advertentieserver. |
| ad_content_url | string | URL van het manifestbestand van de advertentie, van de reactie van de advertentieserver. |
| **†** ad_content_url_actual | string | URL van het ingevoegde manifestbestand van de advertentie. Leeg voor TRACE_AD_REDIRECT. |
| ad_system_id | string | Systeem toevoegen, van de reactie van de advertentieserver (Auditude indien niet opgegeven). |
| ad_id | string | Id van de advertentie, van de reactie van de advertentieserver. |
| creative_id | string | Id van creatief, van de advertentieknooppunt, van de reactie van de advertentieserver. |
| **†** ad_call_id | string | Niet gebruikt. Gereserveerd voor toekomstig gebruik. |
| delta | integer | Tijd (milliseconden) die door deze gebeurtenis wordt genomen. |
| **†** misc | string | Reden dat advertentie is overgeslagen. |

**†** `ad_content_url_actual`,  `ad_call_id`en  `misc` velden zijn optioneel.

>[!NOTE]
>
>Voor `TRACE_AD_RESOLVE` en `TRACE_AD_INSERT` is de URL in het veld `ad_content_url_actual` voor de getranscodeerde code en indien beschikbaar. Anders is het veld leeg voor `TRACE_AD_RESOLVE` of hetzelfde als `ad_content_url` voor `TRACE_AD_INSERT`.

Een voorbeeld:

```shell
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

<!-- ### TRACE_TRACKING_URL records {#trace-tracking-url-records}

Records of this type log the results of manifest server ad requests. Fields beyond `TRACE_TRACKING_URL` appear in the order shown in the table, separated by tabs.

| Field | Type | Description |
|---|---|---|
| pts | number | Program timestamp. Time within video to call the URL. |
| ad_system | string | Ad system (auditude or freewheel) |
| url | string | URL pinged |
| status | string | HTTP status returned from the ping |

```shell
2015-06-04T23:24:42.000-0700 1426742736208 3086f5cd . . . 12345 TRACE_TRACKING_URL 0.000000 ExampleSystem https://localhost/index.php?stream:test#8.1433485415; sid:3086f5cd . . .;pts:0 200
```

-->

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE records {#trace-transcoding-no-media-to-transcode}

Records van dit type registreren een ontbrekend en creatief bestand. Het enige veld buiten `TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE` verschijnt in de tabel.

| Veld | Type | Beschrijving |
|---|---|---|
| ad_id | string | Volledig gekwalificeerde advertentie-id (FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID..\] \] Q_AD_ID: PROTOCOL:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\] \] PROTOCOL: AUDITUDE, VAST) |

De verslagen van dit type registreren de resultaten van het transcoderen verzoeken die de manifestserver naar CRS verzendt. De gebieden voorbij `TRACE_TRANSCODING_REQUESTED` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| ad_id | string | Volledig gekwalificeerde advertentie-id |
| ad_manifest_url | string | URL van het manifestbestand van de advertentie, van de reactie van de advertentieserver |
| creative_type | string | Type media |
| vlaggen | string | ID3 geeft aan of de transcoderingsaanvraag een verzoek bevat om een ID3-tag toe te voegen |
| target_duration | string | Doelduur (seconden) van de getranscodeerde creatieve waarde |

De verslagen van dit type wijzen op een verzoek om server zij het volgen te doen. De gebieden voorbij `TRACE_TRACKING_REQUEST` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| tracking_url_count | integer | Aantal URL&#39;s die worden bijgehouden |
| start | zweven | Begintijd van PTS-fragment (seconden met precisie milliseconde) |
| end | zweven | Eindtijd van PTS-fragment (seconden met precisie milliseconde) |

Records van dit type bevatten een URL voor het bijhouden van de serverzijde. De gebieden voorbij `TRACE_TRACKING_REQUEST_URL` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| tijdstempel | zweven | Tijd (seconden, met precisie 0,001) binnen de playbackzitting om het volgen URL te pingelen. |
| ad_system | string | Advertentiesysteem (bijvoorbeeld auditude) |
| url | string | URL die moet worden geping |

Records van dit type logbestand vragen de manifestserver om `WEBVTT` bijschriften. De gebieden voorbij `TRACE_WEBVTT_REQUEST` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| status | string | Geretourneerde HTTP-statuscode |
| vtt_uri | string | URL voor aanvraag |
| start | zweven | Starttijd splitsen (seconden met precisie milliseconde) |
| end | zweven | Eindtijd splitsen (seconden met milliseconde-precisie) |

Records van dit type logreacties die de manifestserver naar clients verzendt in `answer` naar aanvragen voor `WEBVTT` bijschriften. De gebieden voorbij `TRACE_WEBVTT_RESPONSE` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| status | string | Geretourneerde HTTP-statuscode |
| reactie | string | Base64-gecodeerde reactie die naar cliënt wordt verzonden |

Records van dit type logreacties op aanvragen die de manifestserver aanbrengt voor `WEBVTT` bijschriften. De gebieden voorbij `TRACE_WEBVTT_SOURCE` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| status | string | Geretourneerde HTTP-statuscode |
| bron | string | Base64-gecodeerde oorspronkelijke VTT-inhoud |

De verslagen van dit type laten de manifestserver toe om gebeurtenissen en informatie te registreren niet anders gepland voor wanneer het advertenties opneemt. Het veld voorbij `TRACE_MISC` bestaat uit een berichttekenreeks. De berichten die zouden kunnen verschijnen omvatten het volgende:

* Toevoegen genegeerd: AdPlacement \[addManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1\]
* AdPlacement adManifestURL= adManifestURL, durationSeconds= seconds, ignore= ignore, redirectAd= redirectAd, priority= priority
* De advertentie is null geretourneerd.
* Toegevoegd.
* Aanroep toevoegen mislukt: foutbericht.
* Gebruiker-Agent toevoegen om onbewerkte manifest te halen: user-agent.
* Cookie toevoegen om Raw-manifest op te halen: Aantal
* Onjuist URL-foutbericht opgevraagd. (Kan URL variant niet parseren)
* Opgeroepen URL: URL retourneert: antwoordcode. (Live URL)
* Opgeroepen URL: Retourcode URL: antwoordcode. (VOD-URL)
* Conflict gevonden tijdens het omzetten van advertenties: een van de middelste of middelste beginuiteinden valt binnen de voorrol of voorrol in de middelste rol (VOD).
* Onverwerkte uitzondering gedetecteerd die door de handler voor URI wordt gegenereerd: verzoek-URL.
* Gereed met het genereren van het manifest van de variant. (Variant)
* Gereed met het genereren van het manifest van de variant.
* Uitzondering bij verwerking van VAST redirect *redirect URL *error: foutbericht.
* Kan de afspeellijst van de advertentie niet ophalen voor de URL van het advertentiemanifest.
* Kan doelmanifest niet genereren. (HLSManifestResolver)
* Kan eerste reactie op advertentie niet parseren: foutbericht.
* Kan *GET|POST *request for path niet verwerken: verzoek-URL. (Live/VOD)
* Kan live manifestverzoek niet verwerken: verzoek-URL. (Live)
* Kan geen variantmanifest retourneren: foutbericht.
* Kan groep-id niet valideren: groep-id.
* Onbewerkte manifest ophalen: inhoud-URL. (Live)
* Na omleiding VAST: URL omleiden.
* Er zijn lege bronnen gevonden. (VOD)
* *nummer* advertenties gevonden. (VOD)
* HTTP-aanvraag ontvangen. (Zeer eerste bericht)
* Dit wordt genegeerd omdat het verschil tussen de tijdsduur van de advertentie (*ad responsduur *sec) en de werkelijke duur van de advertentie (*actual duration *sec) groter is dan de limiet. (HLSManifestResolver)
* Negeren is gelukt zonder id-waarde. (GroupAdResolver.java)
* Negeren van een geldige tijdwaarde: *time *for availId = geldige id.
* Negeren van een geldige waarde voor de duur: *duration *for availId = avail ID.
* Nieuwe sessie initialiseren. (Variant)
* Ongeldige HTTP-methode. Het moet een GET zijn. (VOD)
* Ongeldige HTTP-methode. Trackingverzoek moet een GET zijn. (Live)
* Ongeldig URL-foutbericht opgevraagd. (Variant)
* Ongeldige groep. (HLSManifestResolver)
* Ongeldig verzoek. Bijschrift is geen geldige aanvraag voor bijhouden. (VOD)
* Ongeldig verzoek. Bijschriftverzoek moet worden ingediend nadat de sessie is ingesteld. (VOD)
* Ongeldig verzoek. Het volgende verzoek moet worden gedaan nadat de zitting wordt gevestigd. (VOD)
* Ongeldige serverinstantie voor overbelastingsgroep-id: groep-id. (Live)
* Limiet voor VAST-omleidingen bereikt - getal.
* Plaatsen van advertentie: URL toevoegen.
* Geen manifest gevonden voor: inhoud-URL. (Live)
* Geen gelijke die voor beschikbare identiteitskaart wordt gevonden: geldige id. (HLSManifestResolver)
* Geen afspeelsessie gevonden. (HLSManifestResolver)
* Bezig met verwerken van VOD-verzoek voor URL voor manifestinhoud.
* Verwerkingsvariant.
* Bezig met verwerken van bijschriftverzoek voor URL voor manifestinhoud.
* Trackingverzoek verwerken. (VOD)
* Leid en reactie leeg om. ( VASTStAX)
* Aanvragen: URL.
* Respons van fout voor GET- verzoek omdat geen playbackzitting werd gevonden. (VOD)
* Respons van een fout voor het verzoek van de GET wegens een interne serverfout terugkeren.
* Respons van fout voor GET- verzoek die een ongeldig middel specificeren: aanvraag-id toevoegen. (VOD)
* Respons van fout voor GET- verzoek die een ongeldige of lege groep ID specificeren: groep-id. (VOD)
* Respons van fout voor het terugkeren van GET verzoek die een ongeldige het volgen positiewaarde specificeren. (VOD)
* Respons van fout voor GET verzoek met ongeldige syntaxis terugkeren - verzoek URL. (Live/VOD)
* Respons van fout voor verzoek met niet gestaafde methode van HTTP terugkeren: GET|POST. (Live/VOD)
* Manifest van cache retourneren. (VOD)
* Server is overbelast. Doorgaan zonder aanvraag voor een advertentie. (Variant)
* Beginnen met genereren van doelmanifest. (HLSManifestResolver)
* Begin genererend variantmanifest van: inhoud-URL. (Variant)
* Begin advertenties in manifest te stikken. (VODHLSResolver)
* Poging om advertentie bij `HH:MM:SS` te naaien: AdPlacement \[adManifestURL= and Manifest URL, durationSeconds= seconds, ignore= ignore, redirectAd= redirect ad, priority= priority.\] \(HLSManifestResolver\)
* Kan geen advertenties ophalen vanwege een ongeldige tijdlijn. Retourneerde de inhoud zonder advertenties. (VOD)
* Kan geen advertenties ophalen. Retourneerde de inhoud zonder advertenties. (VOD)
* Kan geen advertentie-query ophalen en er is geen inhoud-URL opgegeven. (VOD)
* Geldige URL ontvangen. (VOD/Variant)
* Variant M3U8 niet gevonden. (Variant)

### TRACE_PLAYBACK_PROGRESS records {#trace-playback-progress-records}

De manifestserver produceert verslagen van dit type wanneer het een signaal over playbackvooruitgang tijdens de server het volgen werkschema ontvangt. De gebieden voorbij `TRACE_PLAYBACK_PROGRESS` verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|---|---|---|
| status | string | HTTP-statuscode |
| bandbreedte | integer | Bandbreedte van de stream |
| pts | integer | PTS-tijd binnen stream |
| ms_time | integer | Tijd waarop URL voor bijhouden van manifestserver is gegenereerd |
| url | string | URL omleiden |
| **The** header_user_agent | string | HTTP User-Agent kopbal |
| **The** header_dnt | integer | HTTP do-not-track header |
| **Wat is** effectief_extern_adres | string | IPv4 effectief ver adres |
| **The** remote_address | string | IPv4-adres op afstand |

**De** laatste vier velden zijn optioneel.

## Meerdere bitsnelheidstreams {#multiple-bitrate-streams}

Clientverzoeken om invoeging van een advertentie geven doorgaans meer dan één bitsnelheid op in de afspeellijst met versies die zijn opgemaakt voor de variant M3U8. De manifestserver genereert en retourneert een nieuw M3U8-bestand met een aparte M3U8-koppeling voor elke bitsnelheid. Er wordt ook een unieke groep-id gegenereerd om deze M3U8s aan elkaar te koppelen.

De manifestserver gebruikt de informatie in het Bootstrap URL-verzoek van de cliënt om de inhoudvariant playlist terug te winnen. Het produceert een nieuwe variant playlist die duidelijke serververbindingen met de stroom-vlakke inhoud bevat. De client gebruikt deze voor het samenstellen en invoegen van aanvragen. De inhoudskoppelingen op streamniveau van de manifestserver hebben de volgende indeling:

```shell
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
{groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **live/**
vodDe manifestserver stelt deze waarde in op basis van het afspeellijsttype van de inhoud: Live/lineair (
`#EXT-X-PLAYLIST-TYPE:EVENT`) of VOD (`#EXT-X-PLAYLIST-TYPE:VOD`)

* **De unieke id van de**
uitgeverAssetIDPublisher voor de specifieke inhoud die in het URL-verzoek van de Bootstrap wordt opgegeven.

* ****
renditionThe manifestserver plaatst dit gebaseerd op 
`BANDWIDTH` -waarde van de inhoudsstroom en gebruikt deze om de bitsnelheid van de advertentie aan te passen aan de bitsnelheid van de inhoud. De bitsnelheid van de advertentie kan de bitsnelheid van de inhoud alleen overschrijden als de advertentie-uitvoering met de laagste bitsnelheid dit doet.

* ****
groupIDTthe manifest server genereert deze waarde en gebruikt deze om ervoor te zorgen dat advertenties consistent worden geplaatst, ongeacht voor welke bitsnelheidsuitvoering de client advertenties aanvraagt.

* **base64-gecodeerde url van de bitsnelheidstreamDe manifestserver URL-safe base64 codeert de absolute URL van de inhoudsstroom.**
Elke stream heeft een eigen URL.

* **Parameters**
voor query-parametersQuery worden opgegeven in de URL-aanvraag voor Bootstrap.
