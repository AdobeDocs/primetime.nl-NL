---
title: Foutopsporingsprogramma voor server Manifest
description: Foutopsporingsprogramma voor server Manifest
products: SG_PRIMETIME
topic-tags: ad-insertion
discoiqdonotlocalize: false
moreHelpPaths: /content/help/en/primetime/morehelp/ad-insertion;/content/help/en/primetime/morehelp/ad-insertion
pagecreatedat: en
pagelayout: video
sidecolumn: left
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '2414'
ht-degree: 0%

---


# Foutopsporingsprogramma voor server wissen {#manifest-server-debugging-tool}

Het het zuiveren hulpmiddel laat uitgevers toe om potentieel dure en toevoegingsproblemen te onderzoeken door het zuiveren informatie te onderzoeken die in echt - tijd door de duidelijke server in de kopballen van HTTP wordt teruggekeerd of, wanneer meer gedetailleerde informatie nodig is, het onderzoeken van zittingslogboeken na het feit. Adobe-partners zoals Akamai kunnen het hulpprogramma gebruiken om fouten op te sporen in hun integratie met Primetime en besluitvorming.

Het hulpmiddel steunt het zuiveren en toevoegings problemen in om het even welke belangrijkste manifestserver en volgende configuraties:

* Client-side tracking met een speler op basis van TVSDK.
* Client-side tracking met een speler die niet is gebaseerd op TVSDK.
* Volgen op de server.

Om al deze gevallen te ondersteunen, vereist het gereedschap geen uitgeverscodes voor de speler of gebruikt het deze.

Wanneer u een manifestserverzitting in werking stelt, kunt u een parameter op verzoekURL plaatsen om het te vragen om het registreren van het zuiveren informatie. Gebruikend verschillende waarden van die parameter, kunt u de manifestserver ook vragen om gespecificeerde stukken van het zuiveren informatie in de kopballen van HTTP terug te keren, maar de kopballen kunnen slechts een beperkte hoeveelheid informatie bevatten. U kunt geloofsbrieven van Adobe verkrijgen om tot volledige logboekdossiers toegang te hebben, die de manifestserver periodiek (bijvoorbeeld, uur) op een archiefserver opslaat. Zodra u geloofsbrieven voor die server hebt, kunt u tot het direct op elk ogenblik toegang hebben.

<!-- You can also see the [server side event tracking captured in the SSAI dashboard](ssai-debugging-dashboard.md).-->

## Opties voor het gereedschap Foutopsporing {#debugging-tool-options}

Wanneer het aanhalen van het het zuiveren hulpmiddel, hebt u verscheidene opties voor welke informatie de duidelijke server in de kopballen van HTTP terugkeert. De opties hebben geen invloed op wat de manifestserver in logbestanden plaatst.

### Het specificeren van ptdebug {#specifying-ptdebug}

Wanneer het in werking stellen zuivert registreren voor een duidelijke serverzitting, kunt u de parameter ptdebug aan het verzoek URL toevoegen om de volgende opties voor de informatie te specificeren die de manifestserver in de kopballen van HTTP terugkeert:

* ptdebug=true Alle records behalve `TRACE_HTTP_HEADER` en de meeste `call/response data` van `TRACE_AD_CALL` records.
* ptdebug=AdCall Only TRACE_AD_*type* (bijvoorbeeld, TRACE_AD_CALL) verslagen.
* ptdebug=Header Only TRACE_HTTP_HEADER records.

De opties hebben geen invloed op de plaatsen van de manifestserver in de logbestanden. Daar hebt u geen controle over, maar de logbestanden zijn tekstbestanden, dus u kunt een groot aantal gereedschappen toepassen om de informatie die u interesseert, te extraheren en opnieuw op te maken.

Hier volgt een voorbeeld van de HTTP-header die wordt geretourneerd wanneer `ptdebug=Header`. Bepaalde lange tekenreeksen hexadecimale cijfers worden voor de duidelijkheid vervangen door `. . .`.

```
X-ADBE-AI-DBG-1 TRACE_MISC    HTTP request received
X-ADBE-AI-DBG-2 TRACE_MISC    Processing Variant
X-ADBE-AI-DBG-3 TRACE_MISC    Valid URL received.
X-ADBE-AI-DBG-4 TRACE_MISC    Initialize new session
X-ADBE-AI-DBG-5 TRACE_MISC    Requesting: /auditude/variant/pubAsset/aHR0cDovL . . .m3u8
 ?u=cecebae . . .&z=189962&pttrackingmode=simple&pttrackingversion=v1
 &ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true
X-ADBE-AI-DBG-6  TRACE_HTTP_HEADER  MAIN  REQUEST  Host    bWFuaWZl. . .
X-ADBE-AI-DBG-7  TRACE_HTTP_HEADER  MAIN  REQUEST  Connection       Y2xvc2U=
X-ADBE-AI-DBG-8  TRACE_HTTP_HEADER  MAIN  REQUEST  Accept   dGV4dC. . .
X-ADBE-AI-DBG-9  TRACE_HTTP_HEADER  MAIN  REQUEST  Cookie   c3NhaT. . .
X-ADBE-AI-DBG-10 TRACE_HTTP_HEADER  MAIN  REQUEST  User-Agent       TW96aWxs. . .
X-ADBE-AI-DBG-11 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Language  ZW4tdXM=
X-ADBE-AI-DBG-12 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Encoding  Z3ppcCwg. . .=
X-ADBE-AI-DBG-13 TRACE_REQUEST_INFO  200   GET
 /auditude/variant/pubAsset/aHR0cD. . ..m3u8
 ?u=cecebae72a919de350b9ac52602623f3&z=189962&pttrackingmode=simple
 &pttrackingversion=v1&ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true   0 0 0   Variant  NA  null  null  127.0.0.1:43357
X-ADBE-AI-DBG-14 TRACE_HTTP_HEADER  MAIN  RESPONSE Content-Type     YXBwbG. . .
X-ADBE-AI-DBG-15 TRACE_HTTP_HEADER  MAIN  RESPONSE Cache-Control    bm8tY2. . .
X-ADBE-AI-DBG-16 TRACE_HTTP_HEADER  MAIN  RESPONSE Access-Control-Allow-Origin    Kg==
X-ADBE-AI-DBG-17 TRACE_MISC   Done
```

## Opmaak van logrecords {#formats-of-log-records}

Elke logrecord heeft een type en een set velden, waarvan sommige optioneel kunnen zijn. De velden van alle records tot het recordtype zijn gelijk. Zij verstrekken een timestamp en informatie over de zitting. Het recordtype identificeert het type gebeurtenis dat wordt geregistreerd, en de verdere gebieden verstrekken informatie over de geregistreerde gebeurtenis.

De structuur van een logrecord is als volgt:

`datetime request_id session_id zone_id record_type` *andere velden.*

| Veld | Type | Beschrijving |
|--- |--- |--- |
| datetime | string | Tijdstempel |
| request_id | string | Verzoek-id gebruikt door de manifestserver (unieke tijdstempel) |
| session_id | string | Sessie-id gebruikt door de manifestserver |
| zone_id | integer | Zone-ID |
| record_type | string | Type gebeurtenis dat wordt geregistreerd |
| overige velden | *** | Afhankelijk van het type gebeurtenis |

### TRACE_REQUEST_INFO records {#trace-request-info-records}

De verslagen van dit type registreren de resultaten van HTTP- verzoeken. De gebieden voorbij TRACE_REQUEST_INFO verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| status | string | Geretourneerde HTTP-statuscode |
| request_method | string | HTTP-methode (GET of POST) |
| request_uri | string | HTTP-aanvraagURI (zonder host) |
| request_length | integer | Duur van aanvraag (bytes) |
| response_length | integer | Lengte van reactie (bytes) |
| delta | integer | Tijd (milliseconden) om verzoek te verwerken |
| module_type | string | Variant, stroom of VOD |
| remote_address_aud_client_ip | string | (zie opmerking) |
| remote_address_x_fwd_for_hdr_key | string | (zie opmerking) |
| remote_host_port | string | (zie opmerking) |

>[!NOTE]
>
>De laatste drie velden zijn optioneel.

Een voorbeeld:

```
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938
TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8
?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER-records {#trace-http-header-records}

Verslagen van dit type de kopballen van HTTP van het logboek tijdens de vraag van HTTP tussen de manifestserver en cliënt, en server, of inhoudsserver ruilden. De gebieden voorbij TRACE_HTTP_HEADER verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| request_type | string | Type verzoek (MAIN of ONBEKEND) |
| request_response | string | Responsheader (verzoek of antwoord) |
| header_name | string | HTTP-headernaam |
| header_value | string | Base64-gecodeerde HTTP-headerwaarde |

>[!NOTE]
>
>De velden request_type en header_value zijn optioneel.

Een voorbeeld:

```
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_MISC
    Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST Cookie  aGRu. . .
2015-03-25T06:10:00.928Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST User-Agent  TW96aW. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Server  bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Content-Type    YXBwb. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Last-Modified   V2VkL. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  ETag    IjIyY2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Vary    QWNjZXB. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Cache-Control   bWF4LW. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Expires V2VkL. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Date    V2VkLCA. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Age MQ==
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Via MS4xIH. . .
```

### TRACE_AD_CALL records {#trace-ad-call-records}

De verslagen van dit type registreren de resultaten van manifestserver en verzoeken. De gebieden voorbij TRACE_AD_CALL verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| status | string | Geretourneerde HTTP-statuscode |
| request_duration | integer | Tijd (milliseconden) van verzoek tot antwoord |
| ad_server_query_url | string | URL voor de advertentievraag, met inbegrip van vraagparameters |
| ad_system_id | string | Systeem toevoegen, van de reactie van de advertentieserver (Auditude indien niet opgegeven) |
| avail_id | string | Id van de zegel, van de advertentie in het contentmanifest-bestand (N.v.t. VOD) |
| avail_duration | getal | Duur (in seconden) van de golf, van de advertentie in het contentmanifest-bestand (N.v.t. VOD) |
| ad_server_response | string | Base64-gecodeerde reactie van een advertentieserver |

Een voorbeeld:

```
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL
200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT, TRACE_AD_RESOLVE en TRACE_AD_REDIRECT records {#trace-ad-insert-trace-ad-resolve-and-trace-ad-redirect-records}

De verslagen van dit type registreren de resultaten van de ad verzoeken die door het verslagtype worden vermeld. Velden buiten het recordtype worden weergegeven in de volgorde die in de tabel wordt weergegeven, gescheiden door tabs.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| status | string | Geretourneerde HTTP-statuscode |
| avail_id | string | ID van de zeepbel, van de advertentie in het content-manifest-bestand (live) of van de manifest-server (VOD) |
| ad_type | string | Type steun (DIRECT of REDIRECT) |
| ad_duration | integer | Duur (seconden) van advertentie, van serverreactie |
| ad_content_url | string | URL van het manifestbestand van de advertentie, van de reactie van de advertentieserver |
| ad_content_url_actual | string | URL van het ingevoegde manifestbestand van de advertentie. Leeg voor TRACE_AD_REDIRECT. |
| ad_system_id | string | Systeem toevoegen, van de reactie van de advertentieserver (Auditude indien niet opgegeven) |
| ad_id | string | ID van de advertentie, van de reactie van de advertentieserver |
| creative_id | string | Id van creatief, van de advertentieknooppunt, van de reactie van de advertentieserver |
| ad_call_id | string | Niet gebruikt. Gereserveerd voor toekomstig gebruik. |
| delta | integer | Tijd (milliseconden) die door deze gebeurtenis is genomen |
| misc | string | Reden dat advertentie is overgeslagen |

>[!NOTE]
>
>De velden ad_content_url_actual, ad_call_id en misc zijn optioneel.

Voor TRACE_AD_RESOLVE en TRACE_AD_INSERT is de URL in het veld ad_content_url_actual voor de getranscodeerde en, indien beschikbaar. Anders is het veld leeg voor TRACE_AD_RESOLVE of gelijk aan ad_content_url voor TRACE_AD_INSERT.

Een voorbeeld:

```
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

### TRACE_TRACKING_URL-records {#trace-tracking-url-records}

De verslagen van dit type registreren de resultaten van manifestserver en verzoeken. De gebieden voorbij TRACE_TRACKING_URL verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| pts | getal | Tijdstempel van programma. Tijd binnen video om de URL aan te roepen. |
| ad_system | string | Toestelsysteem (auditief of vrijwiel) |
| url | string | URL gepingd |
| status | string | De status van HTTP die van pingel is teruggekeerd |

Een voorbeeld:

```
2015-06-04T23:24:42.000-0700    1426742736208     3086f5cd . . .    12345    TRACE_TRACKING_URL
    0.000000    ExampleSystem    https://localhost/index.php?stream:test#8.1433485415;
    sid:3086f5cd . . .;pts:0    200
```

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE records {#trace-transcoding-no-media-to-transcode-records}

Records van dit type registreren een ontbrekend en creatief bestand. Het enige veld buiten TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE wordt in de tabel weergegeven.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| ad_id | string | Volledig gekwalificeerde advertentie-id `(FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\]\]` Q_AD_ID: `PROTOCOL:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\]\]` PROTOCOL: AUDITUDE, VAST) |

### TRACE_TRANSCODING_REQUESTED records {#trace-transcoding-requested-records}

De verslagen van dit type registreren de resultaten van het transcoderen verzoeken die de manifestserver naar CRS verzendt. De gebieden voorbij TRACE_TRANSCODING_REQUESTED verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| ad_id | string | Volledig gekwalificeerde advertentie-id |
| ad_manifest_url | string | URL van het manifestbestand van de advertentie, van de reactie van de advertentieserver |
| creative_type | string | Type media |
| vlaggen | string | ID3 geeft aan of de transcoderingsaanvraag een verzoek bevat om een ID3-tag toe te voegen |
| target_duration | string | Doelduur (seconden) van de getranscodeerde creatieve waarde |

### TRACE_TRACKING_REQUEST-records {#trace-tracking-request-records}

De verslagen van dit type wijzen op een verzoek om server zij het volgen te doen. De gebieden voorbij TRACE_TRACKING_REQUEST verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| tracking_url_count | integer | Aantal URL&#39;s die worden bijgehouden |
| start | zweven | Begintijd van PTS-fragment (seconden met precisie milliseconde) |
| end | zweven | Eindtijd van PTS-fragment (seconden met precisie milliseconde) |

### TRACE_TRACKING_REQUEST_URL-records {#trace-tracking-request-url-records}

Records van dit type bevatten een URL voor het bijhouden van de serverzijde. De gebieden voorbij TRACE_TRACKING_REQUEST_URL verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| tijdstempel | zweven | Tijd (seconden, met precisie 0,001) binnen de playbackzitting om het volgen URL te pingelen |
| ad_system | string | Advertentiesysteem (bijvoorbeeld auditude) |
| url | string | URL die moet worden geping |

### TRACE_WEBVTT_REQUEST-records {#trace-webvtt-request-records}

De verslagen van dit typelogboek verzoeken de manifestserver voor titels WEBVTT maakt. De gebieden voorbij TRACE_WEBVTT_REQUEST verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| status | string | Geretourneerde HTTP-statuscode |
| vtt_uri | string | URL voor aanvraag |
| start | zweven | Starttijd splitsen (seconden met precisie milliseconde) |
| end | zweven | Eindtijd splitsen (seconden met milliseconde-precisie) |

### TRACE_WEBVTT_RESPONSE records {#trace-webvtt-response-records}

Registreert ``of ``dit ``type ``log ``responses ``de ``manifest ``server ``sends ``naar ``clients ``in `` `answer` ``naar ``requests `` `for` ``WEBVTT ``bijschriften. De gebieden voorbij TRACE_WEBVTT_RESPONSE &quot;verschijnen in de orde die in de lijst wordt getoond, gescheiden `by`lusjes.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| status | string | Geretourneerde HTTP-statuscode |
| reactie | string | Base64-gecodeerde reactie die naar cliënt wordt verzonden |

### TRACE_WEBVTT_SOURCE records {#trace-webvtt-source-records}

Verslagen van dit type logboekreacties op verzoeken de manifestserver voor titels WEBVTT maakt. De gebieden voorbij TRACE_WEBVTT_SOURCE verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| status | string | Geretourneerde HTTP-statuscode |
| bron | string | Base64-gecodeerde oorspronkelijke VTT-inhoud |


### TRACE_MISC-records {#trace-misc-records}

De verslagen van dit type laten de manifestserver toe om gebeurtenissen en informatie te registreren niet anders gepland voor wanneer het advertenties opneemt. Het gebied voorbij TRACE_MISC bestaat uit een berichtkoord. De berichten die zouden kunnen verschijnen omvatten het volgende:

* Toevoegen genegeerd:AdPlacement `[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1]`
* AdPlacement adManifestURL=*adManifestURL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirectAd*, priority=*priority a9/>*
* De advertentie is null geretourneerd.
* Toegevoegd.
* Aanroep toevoegen mislukt: *foutbericht*.
* Gebruiker-Agent toevoegen om onbewerkte manifest te halen: *user-agent*.
* Cookie toevoegen om Raw-manifest op te halen: [cookie]
* Onjuiste URL *opgevraagd URL-foutbericht*. (Kan URL variant niet parseren)
* Opgeroepen URL: URL *retourneert: responscode*. (Live URL)
* Opgeroepen URL: URL *retourcode: responscode*. (VOD-URL)
* Conflict gevonden tijdens het omzetten van advertenties: een van de middelste of middelste beginuiteinden valt binnen de voorrol of voorrol in de middelste rol (VOD).
* Onverwerkte uitzondering gedetecteerd die door de handler voor URI wordt gegenereerd: *verzoek URL*.
* Gereed met het genereren van het manifest van de variant. (Variant)
* Gereed met het genereren van het manifest van de variant.
* Uitzondering bij verwerking van VAST redirect *redirect URL *error: *foutbericht*.
* Kan de afspeellijst van de advertentie niet ophalen voor *en manifest-URL*.
* Kan doelmanifest niet genereren. (HLSManifestResolver)
* Kan eerste reactie op advertentie niet parseren: *foutbericht*.
* Kan *GET|POST *request for path niet verwerken: *verzoek URL*. (Live/VOD)
* Kan live manifestverzoek niet verwerken: *verzoek URL*. (Live)
* Kan geen variantmanifest retourneren: *foutbericht*.
* Kan groep-id niet valideren: *groep-id*.
* Onbewerkte manifest ophalen: *inhoud-URL*. (Live)
* Na omleiding VAST: *URL omleiden*.
* Er zijn lege bronnen gevonden. (VOD)
* *nummer *advertenties gevonden. (VOD)
* HTTP-aanvraag ontvangen. (Zeer eerste bericht)
* Dit wordt genegeerd omdat het verschil tussen de tijdsduur van de advertentie (*ad responsduur *sec) en de werkelijke duur van de advertentie (*actual duration *sec) groter is dan de limiet. (HLSManifestResolver)
* Negeren is gelukt zonder id-waarde. (GroupAdResolver.java)
* Negeren van een geldige tijdwaarde: *time *for availId = *avail ID*.
* Negeren van een geldige waarde voor de duur: *duration *for availId = *avail ID*.
* Nieuwe sessie initialiseren. (Variant)
* Ongeldige HTTP-methode. Het moet een GET zijn. (VOD)
* Ongeldige HTTP-methode. Trackingverzoek moet een GET zijn. (Live)
* Ongeldige URL *opgevraagd URL-foutbericht*. (Variant)
* Ongeldige groep. (HLSManifestResolver)
* Ongeldig verzoek. Bijschrift is geen geldige aanvraag voor bijhouden. (VOD)
* Ongeldig verzoek. Bijschriftverzoek moet worden ingediend nadat de sessie is ingesteld. (VOD)
* Ongeldig verzoek. Het volgende verzoek moet worden gedaan nadat de zitting wordt gevestigd. (VOD)
* Ongeldige serverinstantie voor overbelastingsgroep-id: *groep-id*. (Live)
* Limiet voor VAST-omleidingen bereikt - *getal*.
* Plaatsen van advertentie: *roep URL* toe.
* Geen manifest gevonden voor: *inhoud-URL*. (Live)
* Geen gelijke die voor beschikbare identiteitskaart wordt gevonden: *geldige ID*. (HLSManifestResolver)
* Geen afspeelsessie gevonden. (HLSManifestResolver)
* Bezig met verwerken van VOD-verzoek voor manifest *content-URL*.
* Verwerkingsvariant.
* Bezig met verwerken van bijschriftverzoek voor manifest *content-URL*.
* Trackingverzoek verwerken. (VOD)
* Leid en reactie leeg om. ( VASTStAX)
* Aanvragen: *URL*.
* Respons van fout voor GET- verzoek omdat geen playbackzitting werd gevonden. (VOD)
* Respons van een fout voor het verzoek van de GET wegens een interne serverfout terugkeren.
* Respons van fout voor GET- verzoek die een ongeldig middel specificeren: *aanvraag-id toevoegen*. (VOD)
* Respons van fout voor GET- verzoek die een ongeldige of lege groep ID specificeren: *groep-id*. (VOD)
* Respons van fout voor het terugkeren van GET verzoek die een ongeldige het volgen positiewaarde specificeren. (VOD)
* Respons van de fout voor het verzoek van de GET met ongeldige syntaxis - *verzoek URL*. (Live/VOD)
* Respons van fout voor verzoek met niet gestaafde methode van HTTP terugkeren: *GET|POST*. (Live/VOD)
* Manifest van cache retourneren. (VOD)
* Server is overbelast. Doorgaan zonder aanvraag voor een advertentie. (Variant)
* Beginnen met genereren van doelmanifest. (HLSManifestResolver)
* Begin genererend variantmanifest van: *inhoud-URL*. (Variant)
* Begin advertenties in manifest te stikken. (VODHLSResolver)
* Poging om advertentie bij `HH:MM:SS` te naaien: AdPlacement \[adManifestURL=*ad Manifest URL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirect ad*, priority=*priority*.\]
* Kan geen advertenties ophalen vanwege een ongeldige tijdlijn. Retourneerde de inhoud zonder advertenties. (VOD)
* Kan geen advertenties ophalen. Retourneerde de inhoud zonder advertenties. (VOD)
* Kan geen advertentie-query ophalen en er is geen inhoud-URL opgegeven. (VOD)
* Geldige URL ontvangen. (VOD/Variant)
* Variant M3U8 niet gevonden. (Variant)

### TRACE_TRACKING_URL-records {#trace-tracking-url-records-1}

De manifestserver produceert verslagen van dit type na het roepen van een volgende URL tijdens de server het volgen werkschema. De gebieden voorbij TRACE_TRACKING_URL verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| pts | getal | PTS-tijd binnen stream |
| ad_system | string | Advertentiesysteem (auditief of vrijloopsysteem) |
| url | string | URL gepingd |
| state | string | HTTP-statuscode |

### TRACE_PLAYBACK_PROGRESS records {#trace-playback-progress-records}

De manifestserver produceert verslagen van dit type wanneer het een signaal over playbackvooruitgang tijdens de server het volgen werkschema ontvangt. De gebieden voorbij TRACE_PLAYBACK_PROGRESS verschijnen in de orde die in de lijst wordt getoond, door lusjes wordt gescheiden.

| Veld | Type | Beschrijving |
|--- |--- |--- |
| status | string | HTTP-statuscode |
| bandbreedte | integer | Bandbreedte van de stream |
| pts | integer | PTS-tijd binnen stream |
| ms_time | integer | Tijd waarop URL voor bijhouden van manifestserver is gegenereerd |
| url | string | URL omleiden |
| header_user_agent | string | HTTP User-Agent kopbal |
| header_dnt | integer | HTTP do-not-track header |
| effective_remote_address | string | IPv4 effectief ver adres |
| remote_address | string | IPv4-adres op afstand |

>[!NOTE]
>
>De laatste vier velden zijn optioneel.

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).
