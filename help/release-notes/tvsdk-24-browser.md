---
title: Opmerkingen bij de release Browser TVSDK 2.4
seo-title: Opmerkingen bij de release Browser TVSDK 2.4
description: Opmerkingen bij de release van TVSDK 2.4 van de browser beschrijven de nieuwe, ondersteunde en niet-ondersteunde functies en de bekende problemen in TVSDK 2.4 van de browser.
seo-description: Opmerkingen bij de release van TVSDK 2.4 van de browser beschrijven de nieuwe, ondersteunde en niet-ondersteunde functies en de bekende problemen in TVSDK 2.4 van de browser.
uuid: 3a1eb1a5-0e72-4658-beeb-bca8816570e7
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: d71886cb-f34b-47b2-9df7-168686478106
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '6834'
ht-degree: 0%

---


# Opmerkingen bij de release van TVSDK 2.4 van browser {#browser-tvsdk-release-notes}

Opmerkingen bij de release van TVSDK 2.4 van de browser beschrijven de nieuwe, ondersteunde en niet-ondersteunde functies en de bekende problemen in TVSDK 2.4 van de browser.

## Inleiding {#introduction}

Browser TVSDK is een toolkit waarmee u geavanceerde functionaliteit voor het afspelen van video, inhoudsbeveiliging en reclame kunt toevoegen aan uw videospelertoepassingen op browserbasis.

Browser TVSDK 2.4 biedt JavaScript API&#39;s voor het bouwen van browsergebaseerde videotoepassingen en biedt ondersteuning voor het afspelen in de volgende modi:

* Alleen HTML5
* HTML5 met automatische fallback
* Flash altijd

Deze release bevat de volgende informatie:

・ [Documentatie voor TVSDK API voor browser](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

・ [Programmeringsgids voor TVSDK-browsers](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf).

・ [TVSDK voor 1.4 DHLS aan Browser TVSDK 2.4 de Gids van de Migratie](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

・ [Converteren van Browser TVSDK 2.4.6 naar versie 2.4.7](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html).

・ Een referentie-implementatie die in de build is opgenomen.

>[!NOTE]
>
>*Voor een volledige lijst van de veiligheidsoverwegingen voor deze versie, zie de overwegingen van de Veiligheid.

## Nieuwe en ondersteunde functies {#what-s-new-and-supported-features}

Deze versie van Browser TVSDK verstrekt nieuwe eigenschappen die u kunt gebruiken om uw videotoepassingen te verbeteren.

**Nieuw in update 2.4.12 (build 204)**

De volgende toevoeging is beschikbaar als deel van Browser TVSDK 2.4.12 Update (Bouwstijl 204):

* Implementatie van volume-API van AdobePSDK.MediaPlayer wordt zodanig gewijzigd dat automatisch afspelen op iOS is toegestaan wanneer het afspelen wordt gedempt.

・ Een nieuwe API, `auditudeSettings.ignoreVPAIDAds`, wordt toegevoegd om het negeren van VPAID-advertenties toe te staan die van de Auditude-server worden ontvangen. De API werkt niet voor Flash Fallback.

**Versie 2.4.11**

De volgende verbeteringen en toevoegingen zijn beschikbaar als onderdeel van de Browser-versie van TVSDK 2.4.11:

・ HLS Live segment failover wordt gesteund voor MSE en Flash fallback wijzen.

・ Ondersteuning voor `AuditudeSettings.creativeRepackagingDomain` API is nu ook beschikbaar voor MSE. Eerder werd deze alleen ondersteund in de fallback-modus Flash.

・ De release bevat oplossingen voor kritieke problemen met klanten. Zie *Vaste problemen* een lijst.

**Versie 2.4.10**

De volgende verbeteringen en toevoegingen zijn beschikbaar als onderdeel van de Browser-versie van TVSDK 2.4.10:

・ TVSDK biedt enableLogging() om de logboekregistratie in of uit te schakelen. Raadpleeg de [API documentatie](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)voor gebruik.

・ TVSDK biedt geen ondersteuning meer voor standaardhoofdstukken bij gebruik van Adobe Analytics. Definieer en beheer hoofdstukken met uw toepassing.

・ De release bevat oplossingen voor kritieke problemen met klanten. Zie *Problemen opgelost *a lijst.

**Versie 2.4.9**

De volgende verbeteringen en toevoegingen zijn beschikbaar als onderdeel van de Browser-versie van TVSDK 2.4.9:

・ HLS VOD en Levende stromen met tijddiscontinuïteit maar zonder discontinuïteitsmarkeringen worden gesteund.

・ ID3 v2.4.0-frames worden ondersteund met Safari-videotag voor HLS VOD- en Live-streams.

・ Veilige implementatie voor het laden van advertenties zorgt ervoor dat aanroepen van advertentieservers worden bijgewerkt om HTTP te beveiligen op basis van API-configuratie. Zie de klassen AdobePSDK.AdvertisingMetadata en AdobePSDK.ForceHttpsAdConfiguration voor meer informatie. Deze functie wordt niet ondersteund in de Flash-fallback-modus.

・ ID-informatie en extensie-informatie met betrekking tot VAST 3.0-reacties worden nu door TVSDK ter beschikking gesteld van de toepassing en kunnen worden gebruikt voor de implementatie van Moat-integratie voor advertentiemetingen. Zie de API van AdobePSDK.NetworkAdInfo voor meer informatie. Dit wordt niet ondersteund in de Flash fallback-modus.

・ De klasse AdobePSDK.ForceHttpsConfiguration is niet meer beschikbaar. Het is opgevolgd door

AdobePSDK.ForceHttpsAdConfiguration-klasse.

・ Er is nu een nieuwe API beschikbaar, AdobePSDK.optimizeFlashCalls, waarmee de aanroepen kunnen worden geoptimaliseerd om de HLS-afspeelervaring in de Flash-fallback-modus te verbeteren. Dit is standaard uitgeschakeld.

**Nieuw in update 2.4.8 (build 6002)**

Deze update bevat oplossingen voor kritieke klantproblemen. Zie *Opgeloste problemen* voor de lijst.

**Versie 2.4.9**

De volgende verbeteringen en toevoegingen zijn beschikbaar als onderdeel van de Browser-versie van TVSDK 2.4.8:

・ De SDK is nu compatibel met Chrome EME en de wijzigingen in de aanbevolen procedures zijn beschikbaar vanaf Chrome v58. Zie [https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)**

・ Het UI-framework biedt nu ondersteuning voor de workflow voor HLS Access DRM op Flash, alleen Advertentie en gerichte informatie.

・ De setDRMAuthenticateData-API wordt toegevoegd aan het UI-framework. Als u streams wilt afspelen die zijn beveiligd met Adobe Access DRM, roept u deze API aan. Het attribuut drmAuthenticateData kan ook worden opgegeven in de speler. Zie [AdobePSDK.videoBehavior ](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html)voor meer informatie.

**Versie 2.4.7**

De volgende functies zijn nieuw in versie 2.4.7:

・ Toevoeging van de UI Configurator in het Kader UI

U kunt de speler op een van de volgende manieren configureren:

・ Een JSON-object gebruiken

・ API&#39;s gebruiken

Browser TVSDK biedt een hulpprogramma **UI Configurator **om het JSON-object te helpen genereren.

In dit hulpmiddel, kunt u diverse montages selecteren, **Test Configuratie **om de montages te verifiëren, en **Download Configuratie **klikken om de montages te downloaden. Nadat u het bestand hebt gedownload, kunt u de inhoud van dit bestand als JSON-object doorgeven aan de API van ptp.videoPlayer.

・ Toevoeging van de MediaPlayerItemConfig-API aan het UI-framework

Verschillende functies, zoals advertentieMetadata, advertentieFactory, enSignalingMode, networkConfiguration, customRangeMetadata, useHardwareDecoder, subscribeTags, adTags, thumbnailScrubber, billingMetricsConfiguration, kunnen worden geconfigureerd via MediaPlayerItemConfig. Zie de documentatie van AdobePSDK.MediaPlayerItemConfig in de [Browser TVSDK API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)* * [documentatie](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html) voor meer informatie.

In het Kader UI, is de manier om netwerkconfiguraties door de spelerconfiguratie over te gaan gewijzigd.

**Versie 2.4.6**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`networkConfiguration: <network configuration object>`

`}`

`};`

**Versie 2.4.7**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`mediaPlayerItemConfig: {`

`networkConfiguration: <network configuration object>`

`}`

`}`

`};`

* Ondersteuning voor DRM- en analyseworkflows in het UI-framework

DRM-configuraties en Analytics Tracking kunnen worden ingeschakeld via het UI-framework.

* Toevoeging van `AdobePSDK.embedSWFinFullScreenDiv` API

Deze nieuwe API biedt de speler-app flexibiliteit voor het selecteren van het div waarin het FlashFallback.swf-bestand kan worden ingesloten.

* De API van `getVersion`klasse `AdobePSDK.MediaPlayer` is vervangen door de klasse `AdobePSDK.Version` voor informatie over de versie van TVSDK. Zie `AdobePSDK.Version` API [hier](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html) voor meer informatie.

**Versie 2.4.6**

De volgende functies zijn nieuw in versie 2.4.6:

* **Browserondersteuning**

Bladeren staat u toe om de knoop.js stijlmodules in browser te gebruiken. U kunt de afhankelijkheden definiëren en Bladeren bundelt alles in één JavaScript-bestand.

* **Facturering**

Met behulp van facturering kan Browser TVSDK gegevens over spelergebruik verzamelen om Primetime-klanten in rekening te brengen.

>[!NOTE]
>
>De afgekeurde opsommingstekens MediaPlayer.Events en afgekeurde constanten in Enum PSDKErrorCode zijn verwijderd in versie 2.4.6. Zie [Omzetten van TVSDK 2.4.5 in versie 2.4.6](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html) voor meer informatie.

**Versie 2.4.5**

De volgende functies zijn nieuw in versie 2.4.5:

* **Opnieuw afspelen en toevoegen van gebeurtenissen**

   Streams voor HLS Full Event Replay (FER) ondersteunen nu resolutie en ad-gedrag. Om deze steun toe te laten, plaats de advertentie signalerende wijze aan `MANIFEST_CUES` wanneer het creëren van het `MediaPlayerItemConfig` voorwerp.

* **MediaplayerView ScalePolicy Support**

   De ontwikkelaars van de toepassing kunnen verschillende scalePolicy voor de mening nu specificeren gebruikend het bezit MediaplayerView scalePolicy.

* **Ondersteuning voor anamorfe inhoud**

   Het afspelen van anamorfe inhoud wordt nu ondersteund bij gebruik van MSE en Flash.

* **Selectieve toepassing van`withCredentials`**

Wanneer `withCredentials` aan waar wordt geplaatst, kan `Access-Control-Allow-Origin` kopbal niet aan een wilde kaart worden geplaatst. Afhankelijk van de reactie van de server stelt Browser-TVSDK het kenmerk `withCredentials` selectief in. Zie [De API-docs van de TVSDK-browser](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html) voor meer informatie over deze ondersteuning.

**Versie 2.4.4**

De volgende functies zijn nieuw in versie 2.4.4:

* **Chromecast-voorbeeldtoepassing**

Deze release biedt ondersteuning voor een toepassings- en afzenderapp die het afspelen van DASH VOD-streams en DASH Widevine-streams met invoeging op de client aantoont.

* **Geavanceerde ondersteuning voor failover**

Deze versie bevat ondersteuning voor geavanceerde failover-gebruiksgevallen (segment- en serverfailover) voor HLS VOD-streams.

**Versie 2.4.3**

De volgende functies zijn nieuw in versie 2.4.3:

* **Aangepaste tags voor DASH VOD**

   Aangepaste inline-tags (gebeurtenissen) kunnen worden geabonneerd op en ontvangen als object TimedMetadata.

* **Terugspelen van streams zonder extensies**

   HLS- en DASH-streams zonder extensies worden nu ondersteund. Voor het manifestdossier, moet resourceType worden gespecificeerd wanneer het laden van het middel. Voor segmenten en VTT-bestanden wordt de responsheader Inhoud-Type gebruikt om het inhoudstype te bepalen.

**Versie 2.4.2**

De volgende functies zijn nieuw in versie 2.4.2:

* **API-pariteit**

Voor een volledige lijst van de API pariteit, zie [TVSDK voor 1.4 DHLS aan Browser TVSDK 2.4 de Gids van de Migratie](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

* **Ondersteuning van Sample-AES**

   Deze release biedt ondersteuning voor het afspelen van met Sample AES gecodeerde inhoud op MSE- en Flash-fallback. De vereiste om AES-inhoud te hosten op beveiligde oorsprong op Google Chrome is verwijderd.

* **Ondersteuning voor AAC-containers**

   Het afspelen van bestanden met de extensie .aac wordt nu ondersteund. Dit kan alleen-audio streams of alternatieve audio zijn.

   >[!NOTE]
   >
   >AC3 en verbeterde AC3 codecs worden nog niet gesteund.

* **Afspelen van samengevoegde stream**

HLS de stromen die door een Netwerk van de Levering van de Inhoud (CDN) worden geleverd kunnen authentificatietokens op manifest en segmentverzoeken voor controle soms gebruiken, en deze tokens kunnen als parameters URL of als koekjeskopballen worden verstrekt. Het afspelen van dergelijke streams wordt nu ondersteund.

**Versie 2.4.1**

De volgende functies zijn nieuw in versie 2.4.1:

* **UI-framework**

Dit framework, dat is ontworpen om de ontwikkeling van de gebruikersinterface voor op JavaScript gebaseerde videospelertoepassingen te versnellen, bestaat uit API&#39;s voor het opnemen van basisbesturingselementen zoals afspelen/pauzeren en volume en voor het eenvoudig toevoegen of verwijderen van elementen zoals scrubbalstatussen en instellingen voor gesloten bijschriften. U kunt het gedrag specificeren verbonden aan controles, douanecontroles tot stand brengen, en de speler UI van een huid. Dit alles gebeurt via het framework, zonder dat de DOM-structuur rechtstreeks hoeft te worden gemanipuleerd.

* **Verbeteringen in het afspelen van HLS voor live streams**

Deze versie ondersteunt onderbrekingen die worden veroorzaakt door het invoegen van advertenties. De tag EXT-PROGRAMM-DATE-TIME, gevolgd door de tag EXT-MEDIA-SEQUENCE, wordt gebruikt om te synchroniseren tussen adaptieve bitsnelheidprofielen voor een vloeiende weergave.

* **VPAID 2.0-ondersteuning**

De videospeler ad-serving interfacedefinitie (VPAID), versie 2.0, biedt gebruikers een rijke mediabeleving en stelt uitgevers in staat om advertenties beter te richten, indrukken bij te houden en te monetiseren, en video-inhoud te monetiseren. Deze release ondersteunt lineaire JavaScript VPAID-advertenties voor video-on-demand (VOD)-inhoud.

* **Aangepaste HLS-tags**

Mediastreams kunnen aanvullende metagegevens in de vorm van tags in het afspeellijst-/manifestbestand bevatten. Met TVSDK van browser kunt u aanvullende tags opgeven en hierop een abonnement nemen. U krijgt een melding wanneer deze tags in het manifest worden weergegeven.

* **Markeertekens toevoegen die op de tijdlijn van de speler worden weergegeven**

Deze release ondersteunt het weergeven van advertentiemarkeringen op de tijdlijn van de speler voor zowel VOD- als Live-inhoud. U kunt dit gedrag zien in de referentiespeler.

**Ondersteund in 2.4**

De volgende functies waren beschikbaar in versie 2.4:

* **MP3-audio afspelen**

   Deze release biedt ondersteuning voor het afspelen van MP3-audio in browsers met MSE (Media Source Extensions) en met de Safari-videotag.

* **Afspelen van MP4-video**

   De volgende functies worden ondersteund:

   * Afspelen via één stream
   * MP4-advertenties vóór en na de rol met advertenties en tracering
   * HLS-advertenties vóór en na de rol met advertentiemogelijkheden en tracering
   * DASH-advertenties vóór en na de rol met advertenties en tekstspatiëring

## Ondersteunde platforms {#supported-platforms}

Browser TVSDK heeft specifieke vereisten voor de niveaus van platforms en software waarop het moet worden uitgevoerd. De volgende platforms en softwareniveaus worden ondersteund:

### Desktopconfiguraties {#desktop-configurations}

* Microsoft Windows 7:

   * Internet Explorer 11+
   * Chroom 33+
   * Firefox 38+

* Microsoft Windows 8.1

   * Internet Explorer 11+
   * Chroom 33+
   * Firefox 38+

* Microsoft Windows 10

   * Rand+

* Apple OS X

   * Safari 9+
   * Chroom 33+
   * Firefox 38+

### Mobiele webconfiguraties {#mobile-web-configurations}

* Android 4.4

   * Systeemeigen browser
   * Chroom 33+

* Android 5.0

   * Oorspronkelijke browser
   * Chroom 33+

* Android 6.0

   * ・ Chrome 33+

* Apple iOS 9

   * Safari 9+
   * Chroom 33+

* Apple iOS 10

   * Safari 9+
   * Chroom 33+

**Google Chromecast (tweede generatie; alleen voor DASH-weergave)**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Technologie</strong> </p> </td> 
   <td><p><strong>Video-tag</strong><sup> 1 voor TVSDK-browser</sup></p> </td> 
   <td><p><strong>Browser TVSDK MSE</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>Standaardtechnologie</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>iOS</p> </td> 
   <td><p>MP4 en HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>-</p> </td> 
   <td><p>Video-tag</p> </td> 
  </tr> 
  <tr> 
   <td><p>Android</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS en DASH</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Apple Safari 8</p> </td> 
   <td><p>MP4 en HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 en HLS</p> </td> 
   <td><p>Video-tag</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS en DASH</p> </td> 
   <td><p>MP4 en HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS en DASH</p> </td> 
   <td><p>MP4 en HLS</p> </td> 
   <td><p>MSE<sup>2</sup></p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 7)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 en HLS</p> </td> 
   <td><p>Flash</p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 8.1)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS, DASH</p> </td> 
   <td><p>MP4 en HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
 </tbody> 
</table>

## Eigenschappenmatrix {#feature-matrix}

Hier volgt een lijst met de ondersteunde en niet-ondersteunde functies voor deze release:

* *MP3-audiofuncties — Core Playback*
* *MP4-videofuncties — Core Playback*
* *MP4-videofuncties — Core Ad Insertion*

>[!NOTE]
>
>*In de onderstaande tabel met functiematrix betekent &#39;Y&#39; dat de functie wordt ondersteund in de huidige versie.*

### MP3-audiofuncties {#mp-audio-features}

**Tabel 1: Core Playback{#table-core-playback}**

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Afspelen | MP3 VOD | Algemeen afspelen (afspelen, pauzeren, zoeken) | Niet ondersteund | Y | Y |

1 De video-tag Browser TVSDK ondersteunt geen streaming en DRM. De codec- en containerondersteuning is niet hetzelfde in alle browsers.

2 Firefox heeft standaard de waarde Flash Player voor versie 41 of eerder.

### MP4-audiofuncties {#mp-audio-features-1}

**Tabel 2: Core Playback**

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Afspelen | MP4 VOD | Algemeen afspelen (afspelen, pauzeren, zoeken) | Niet ondersteund | Y | Y |

**Tabel 3: Core Ad Insertion**

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | MP4 VOD | Pre-roll (MP4) | Niet ondersteund | Y | Y |
| Ad Insertion | MP4 VOD | Narol (MP4) | Niet ondersteund | Y | Y |

Zie hieronder voor meer informatie over ondersteuning van HLS- of DASH-functies.

## HLS-functiematrix {#hls-feature-matrix}

Hier is de eigenschapmatrijs voor de eigenschappen HLS in Browser TVSDK.

* *HLS Core-afspelen*
* *HLS Geavanceerde afspeelfuncties*
* *Functies voor beveiliging van HLS-inhoud*
* *HLS Core- en invoegfuncties*
* *HLS Geavanceerde functies voor het invoegen van afbeeldingen*
* *HLS-integratie*

>[!NOTE]
>
>*In de onderstaande tabel met functiematrix betekent &#39;Y&#39; dat de functie wordt ondersteund in de huidige versie.*

### HLS-functies {#hls-features}

De volgende functies worden ondersteund:

**Tabel 4: HLS Core-afspelen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android-chroom</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Algemeen afspelen (afspelen, pauzeren, zoeken)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Algemeen afspelen (afspelen, pauzeren en zoeken)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adaptieve bitsnelheid</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>608/708 bijschriften</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Alleen VOD</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Kennelijke failover</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Geavanceerde failover</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>QoS- en spelersmeldingen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperkte QoS-ondersteuning</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Ondersteuning voor cookie headers</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Parameters voor bufferbesturing instellen</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Aangepast instellen</p> <p>besturingselementen voor bitsnelheid</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Aangepaste tags</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td>Geluid met late binding</td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 omleiding</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 5: Geavanceerde HLS-afspeelfuncties**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android-chroom</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Afspelen bij verschuiving</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Alleen-audio afspelen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Steen afspelen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Vloeiende steen afspelen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3-parsering</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Ondersteuning van discontinue markeertekens</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Verwarmde stromen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Facturering</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 6: Functies voor beveiliging van HLS-inhoud**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android-chroom</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhoud beschermen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhoud beschermen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhoud beschermen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>Adobe Access</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
   <td><p>FairPlay</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 7: HLS Core- en invoegfuncties**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android-chroom</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Pre-roll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Middenrol (HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Narol (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Resolutie en gedrag toevoegen</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Standaardbeleid en standaardbeleid</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2,0/3,0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Creative Repackaging (MP4 naar HLS)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 8: HLS Geavanceerde functies voor het invoegen van afbeeldingen**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android-chroom</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Alleen advertentie</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Doelparameters</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Aangepaste parameters</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Aangepast advertentiebeleid</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Lazy en laden</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
   <td><p>Beperking van Platform</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Companion ads, banneradvertenties, klikbare advertenties</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>SWF</p> </td> 
   <td><p>JavaScript</p> </td> 
   <td><p>JavaScript</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 9: HLS-integratie{#table-hls-integrations}**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android-chroom</strong></p> </td> 
   <td><p><strong>HTML5: Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Integraties</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adobe Analytics VHL-integratie</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## DASH-functiematrix {#dash-feature-matrix}

Hier is de eigenschapmatrijs voor de eigenschappen DASH in Browser TVSDK.

・ *DASH Core-afspeelfuncties*

・ *Geavanceerde afspeelfuncties voor DASH*

・ *Beschermingsfuncties voor DASH-inhoud*

・ *DASH Core- en invoegfuncties*

・ *Geavanceerde DASH-invoegfuncties*

・ *DASH-integratie*

>[!NOTE]
>
>In de onderstaande tabel met functiematrix betekent een Y dat de functie wordt ondersteund in de huidige versie.

### DASH-functies {#dash-features}

De volgende functies worden ondersteund:

**Tabel 10: DASH Core-afspeelfuncties**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android-chroom</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Algemeen afspelen (afspelen, pauzeren, zoeken)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Algemeen afspelen (afspelen, pauzeren en zoeken)</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adaptieve bitsnelheid</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>608/708 bijschriften</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Failover</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>QoS- en spelersmeldingen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Ondersteuning voor cookie headers</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Parameters voor bufferbesturing instellen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Aangepaste besturingselementen voor bitsnelheid instellen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Aangepaste tags (EventStream)</p> </td> 
   <td><p>Alleen VOD (inline)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Laatst gebonden audio</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 omleiding</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 11: Geavanceerde afspeelfuncties DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><strong>HTML5 FF, IE, Chrome, Android-chroom</strong></td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Afspelen bij verschuiving</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Alleen-audio afspelen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Steen spelen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Vloeiende steen afspelen</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3-parsering</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Ondersteuning voor meerdere perioden</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Verwarmde stromen</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Afspelen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Facturering</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 12: Functies voor DASH-inhoudsbeveiliging**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android-chroom</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhoud beschermen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhoud beschermen</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Inhoud beschermen</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Widevine op Chrome, Firefox 47 en hoger, en Chromecast</p> <p>・ PlayReady in Internet Explorer op Windows 8.1 en Edge</p> <p>・ Primetime DRM voor Windows Firefox (alleen video)</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 13: DASH Core- en invoegfuncties**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android-chroom</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Pre-roll (MP4/DASH)</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Middenrol (DASH)</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Narol (MP4/DASH)</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Resolutie en gedrag toevoegen</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Standaardbeleid en standaardbeleid</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2,0/3,0</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Creative Repackaging (MP4 naar DASH)</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 14: Geavanceerde DASH-functies en invoegfuncties**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>HTML5</strong> FF, IE, Chrome, Android-chroom</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Alleen advertentie</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Doelparameters</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Aangepaste parameters</p> </td> 
   <td><p>Alleen VOD</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Aangepast advertentiebeleid</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Lazy en laden</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Companion-advertenties, banneradvertenties, klikbare advertenties</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>Niet ondersteund</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 15: DASH-integratie**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Categorie</strong></p> </td> 
   <td><p><strong>Inhoudstype</strong></p> </td> 
   <td><p><strong>Functie</strong></p> </td> 
   <td><p><strong>HTML5: FF, IE, Chrome, Android-chroom</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Integraties</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adobe Analytics VHL-integratie</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## Opgeloste problemen {#issues-fixed}

**Problemen opgelost in 2.4.12-update (build 204)**

De volgende problemen zijn opgelost in de Browser-versie van TVSDK versie 2.4.12 Update (build 204):

・ **21647**- TVSDK moet het automatisch afspelen van video op iOS-apparaten mogelijk maken wanneer de audio wordt gedempt.

・ **21465** - De Afgewezen Toegang van het Systeem van de Sleutel van de Fout wordt ontvangen wanneer het spelen van een DRM-Beschermde DASH stroom nadat een Levende DASH stroom wordt gespeeld.

・ **21442**- Inhoud automatisch afspelen op iOS-web inschakelen nadat een preroll-advertentie met een gebruikersbeweging is afgespeeld.

・ **21240**- Geleverde API om VPAID-advertenties te filteren die vanuit Auditude/VMAP zijn geparseerd.

**Opgeloste problemen in versie 2.4.11**

De volgende problemen zijn opgelost in Browserversie 2.4.11 van TVSDK:

**Belangrijkste afspeelfuncties:**

・ **19192**: TVSDK implementeert nu TextFormat:bottomInset en TextFormat:safeArea. Dankzij deze verbeteringen kunnen Closed Captions opnieuw worden geplaatst als de besturingsbalk op het scherm wordt weergegeven.

・ **21009**: Gesloten bijschriften blijven op het scherm staan als er wordt gezocht naar een onderbreking totdat er nieuwe bijschriften verschijnen.

・ **21141**: Het terugzoeken wordt afgewezen vanwege een zeldzame omstandigheid tijdens het toevoegen van het segment.

・ **21142**: U kunt zoekbare afspeelbereiken beschikbaar maken wanneer de speler zich in de status INITIALIZED bevindt. Vanwege deze wijzigingen wordt het starten van de sessie op positie nu ondersteund.

・ **21363**: 608/708 gesloten bijschriften gaan niet meer synchroon nadat ze voor DASH-streams zijn geplaatst.

**Toevoegingsfuncties:**

・ **21179**: Problemen met middelste rol (lange pauzes, zwarte frames) met VOD-inhoud worden nu opgelost door de eigenschap ad.primaryAsset.adParameters correct in te stellen.

・ **21257**: Het MP4-bestand met de hoogste bitsnelheid wordt geselecteerd voor transcodering als MP4 geen geldig mime-type is en de functie voor creatief opnieuw verpakken is ingeschakeld.

・ **21361**: TVSDK geeft nu systeem- en creatieve id van de VAST-reactie door als queryparameters in de aanvraag voor creatieve pakketten ter ondersteuning van aanvullende normalisatieregels.

**Problemen opgelost in versie 2.4.10**

De volgende problemen zijn opgelost in Browserversie 2.4.10 van TVSDK:

**Belangrijkste afspeelfuncties:**

・ **21060**: Ongeldige codec fout die met stromen HLS wordt geworpen die discontinuïteit bevatten en de dozen van ISO BMFF lopen aan eind van stroom.

・ **21045**: Automatisch afspelen werkt niet op iOS nadat het eerste afspelen van video in een afspeellijst is voltooid.

・ **20975**: De framesnelheid wordt als NaN geretourneerd door de QoS-provider in Chrome-browser.

・ **20823**: Niet-ondersteunde codec-fout gegenereerd bij aangetroffen segmenten zonder gegevens.

・ **20769**: SDK begint nu met de huidige bitsnelheid bij zoeken in plaats van onmiddellijk over te schakelen op basis van ABR-beleid.

・ **20031**: In de staande modus van IE11 (Windows 8.1) wordt het videoscherm klein. Functie voor inhoudsbeveiliging:

・ **19316**: Skip segmenten die decryptie in het geval van stromen HLS AES-128 ontbreken.

**In versie 2.4.9 opgeloste kwesties**

De volgende problemen zijn opgelost in Browserversie 2.4.9 van TVSDK:

**Belangrijkste afspeelfuncties:**

・ **13407**: DASH-streams kunnen stagneren als Firefox stopt met het verzenden van de gebeurtenis &quot;ontimeupdate&quot; tijdens het afspelen.

・ **16380**: Tijdens het afspelen van video-inhoud via Muxed Audio Video van segmenten met niet-overeenkomende begintijden via MSE, accumuleert de fout Audiosynchronisatie tussen vertegenwoordigingen op ABR-switches, wat uiteindelijk resulteert in Fout (Chromiumprobleem #663686).

・ **17985**: Bij het afspelen van bepaalde ISO-BMFF-stream op Firefox-browser, blijft het afspelen vastzitten (Firefox-uitgave #1342913). Dit is opgelost sinds Firefox v53.

・ **19141**: Uncaught (in promise) ReferenceError: width is not define.

・ **18997, 19299**: Probleem met videoflikkering bij segmentgrens. Dit gebeurde omdat SDK de verschuiving van de samenstellingstijd van de laatste steekproef niet correct berekende.

・ **19780**: Het afspelen begint niet voor HLS-inhoud en HLS-advertentie op Firefox v53 (Firefox-uitgave #354653).

・ **20046**: Datum en tijd van programma wordt ontvangen als sleutel in plaats van als waarde wanneer ontvangen als getimed metagegevensobject.

・ **20047**: useDefaultResizeHandler genereert een fout met Flash fallback.

・ **20179**: Flash fallback werkt niet met Flash Player 25.0.0.171.

・ **20293**: Firefox stopt met het bufferen van gegevens voor bepaalde HLS-streams die leiden tot stagnatie.

・ **20626**: Player genereert een mediacodeerfout op Chrome als gevolg van een onjuiste afhandeling van videosamples met een duur van nul.

・ **20078**: Het afspelen van afspeelstallen bij de browserfout &#39;QuotaExceeded&#39;.

・ **18639**: In HLS Live Stream 608 CC wordt tekst soms weergegeven als verkeerd gespeld.

・ **20028**: De grootte van ClosedCaptions-parameter wijzigt de tekengrootte niet.

・ **20613**: Gesloten bijschriftvakken overlappen elkaar waardoor ze onleesbaar worden.

**Core Ad Insertion (CSAI)-functies:**

・ **20043**: Ontbrekende ADD-indruk en opvolging van advertenties met meerdere advertenties en omleidingen van derden.

・ **2004**: Als u creatief opnieuw verpakken gebruikt, moeten alle advertenties in het ad-einde met succes worden herverpakt om te voorkomen dat het ad-einde volledig wordt verwijderd.

・ **20097**: Het afspelen van advertenties wordt overgeslagen en de hoofdinhoud wordt onmiddellijk hervat in plaats van te wachten op een time-out van 20 seconden als ad-manifest niet beschikbaar is.

**Problemen opgelost in versie 2.4.8 Update (build 6002)**

De volgende problemen zijn opgelost in de Browser-versie van TVSDK versie 2.4.8-update (build 6002):

・ **14126:** Afspelen kan op Firefox vastlopen (uitgave #1316024) vanwege interne tussenruimte in MSE-bronbuffer. Probeer te zoeken om het afspelen te hervatten

・ **19608:** Repareren om de tijdverschuivingswaarde van Auditude VMAP reactie na te leven.

・ **19635:** Oplossingen voor videoband in Internet Explorer 11 in Windows 10.

・ **19761:** Oplossingen voor ABR-problemen met HLS.

・ **19780:** Hiermee wordt het afspelen van de advertentie gecorrigeerd met HLS-inhoud die is afgebroken in Mozilla Firefox v53.

・ **19877 en 19744:** De problemen verhelpen de inconsistentie bij het selecteren van bitsnelheid na een zoekbewerking. De bitsnelheidselectie bij zoeken is nu de lagere waarde van de huidige bitsnelheid en de bitsnelheid bij het opstarten.

・ **19881:** Afspelen vastgezet en bufferbedekking wordt gedurende 3-4 keer weergegeven nadat het zoeken is uitgevoerd.

・ **19884:** Bevestig naleving van Chrome 59 Beta Verified Media Path (VMP) vereisten. bTVSDK kon Widevine DRM-inhoud afspelen met Chrome 59 Beta.

・ **19916:** DRM playback op UI-Kader werd gebroken. Nu, roept het verwervingLicense aan zelfs als er geen beleid in de meta-gegevens is.

**In versie 2.4.8 opgeloste problemen**

De volgende problemen zijn opgelost in de Browser-versie van TVSDK 2.4.8:

・ **10075**: Bij het zoeken vóór de tijdlijn is de gebeurtenis play complete niet ontvangen op Firefox en Chrome en is de gebeurtenis seek niet ontvangen op Firefox.

・ **15775**: De gebeurtenis Play complete is niet ontvangen in Windows 8.1 Internet Explorer.

・ **17306**: Voor SSAI-streams wordt het afspelen ondersteund. Het bijhouden van vastgezette advertenties wordt niet ondersteund.

・ **19142**: Bij terugspoelen blijft de videospeler soms in de bufferstatus.

・ **19218**: Advertentiemarkeringen zijn niet beschikbaar via UI-framework.

・ **19219**: Alleen afspelen toevoegen werkt niet via het gebruikersinterface-framework.

・ **19222**: AES-128 sleutel wordt gevraagd eens voor playlist en de verdere verzoeken worden gediend van het geheime voorgeheugen. Eerder werd het aangevraagd voor elk segment.

・ **19597**: &quot;Uncaught TypeError: Kan eigenschap &#39;log&#39; van undefined niet lezen. Dit is in de kanariële builds van Chrome waargenomen.

・ **19605**: adRequestDomain was niet beschikbaar in de modus Flash fallback.

・ **19608**: VMAP-advertenties werden niet ingevoegd voor HLS Live-streams. SDK neemt nu de actiemarkeringen in overweging en vertrouwt niet op verschuivingswaarden voor de tijd in VMAP-reacties.

・ **19637**: Als u alleen het afspelen toevoegt, treedt er een scriptfout op aan het einde van de advertentie.

・ **19732**: CRS playlist verzoeken mislukten met 404 fout. De verzoeken 1401 en 1403 van Browser TVSDK worden nu bijgewerkt om dat te behandelen.

・ **19762**: verwervingLicense werd vóór setAuthenticationToken aangeroepen omdat er een geldige licentie werd geretourneerd, ongeacht de geldigheid van het token. Dit is nu opgelost en verwervingLicense wordt alleen aangeroepen na de reactie setAuthenticationToken.

**In versie 2.4.7 opgeloste kwesties**

De volgende problemen zijn opgelost in versie 2.4.7:

・ **8397**: Live HLS-streams die via Adobe Media Server worden gegenereerd, worden mogelijk niet afgespeeld als de segmenten niet met een keyframe beginnen.

・ **13606**: Problemen met meerdere zoekopdrachten zijn opgelost voor HLS-stroom in Chrome-browser.

・ **14807**: Als in Chrome de zoekactie of pauze direct wordt geactiveerd na het afspelen(), kan het afspelen stoppen met de fout DOMException: De aanvraag play() is onderbroken door een aanroep..(Chroomnummer nr. 593273).

・ **19085**: MediaPlayer-parameters zoals volume, abrControlParameters en ccStyle worden niet ingesteld op Standaardwaarden bij het opnieuw instellen van de speler.

**Opgeloste problemen in versie 2.4.6**

Het volgende probleem is opgelost in versie 2.4.6:

・ **18093**: TimedMetadata voor de tag naast de geabonneerde tag wordt geretourneerd wanneer u Flash Player versie 24 gebruikt in de modus Flash fallback.

**Opgeloste problemen in versie 2.4.4**

De volgende problemen zijn opgelost in versie 2.4.4:

・ **8711**: Bij MSE worden bijschriften van 608/708 standaard uitgevuld.

・ **13934**: ABR-instellingen voor advertenties zijn niet van toepassing bij het afspelen met actieve HLS-streams.

・ **14079**: Langdurigheid voor HLS Live-streams met een laag DVR-venster kan mislukken, omdat het afspelen mogelijk achterop raakt als gevolg van netwerklatentie. Klik op het actieve punt om het afspelen te hervatten.

・ **15037**: De samples die met het gebruikersinterface-framework van de speler worden geleverd, werken niet in Microsoft Internet Explorer 10 in Windows 7.

・ **15913**: Voor HLS VOD stromen, op Chrome, zal de stroom niet spelen als de duidelijke reactie 304 niet wordt gewijzigd. Dit is vastgesteld sinds Chrome v55 (Chromiumnummer 633696).

・ **16103**: Bij Android Chrome kan het afspelen onder lage bandbreedteomstandigheden stagneren bij de Uncaught TypeError: Kan eigenschap &#39;programDateTime&#39; van niet-gedefinieerde fout niet lezen.

・ **16265**: Voor HLS VOD- en Live-streams werkt het zoeken naar discontinuïteit niet.

・ **16709**: Als u de HLS Live-stream hervat met PDT en discontinue markering, kan de speler vastlopen in de buffering.

## Bekende problemen en beperkingen {#known-issues-and-limitations}

De beperkingen en bekende problemen in Browser TVSDK worden hieronder vermeld.

**Tabel 16: Core Playback-functies**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhoudstype</strong></td> 
   <td><strong>Functie</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (alleen DASH-weergave)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Algemeen afspelen (afspelen, pauzeren, zoeken)</td> 
   <td><p>・ Andere media-indelingen dan HLS worden niet ondersteund.</p> <p>8799: Bij het terugkoppelen van Flash wordt niet rekening gehouden met gemengde inhoud en daarom moet ervoor worden gezorgd dat inhoud, advertentie en andere URL's niet leiden tot gemengde inhoud (beveiligde en onveilige inhoud samen).</p> <p>・ 19271: Afspelen via gebruikersinterface wordt niet ondersteund in de Flash fallback-modus.</p> <p>・ Flash fallback werkt niet in Microsoft Internet Explorer 8 en 9 in Windows 7 omdat deze versies niet door de SDK worden ondersteund.</p> <p>・ 20262: Met fallback voegt u aangepaste parameters toe aan de lijst met doelinfo. Ook de prioriteitsvolgorde van aangepaste parameters verschilt in het geval van Flash en MSE.</p> <p>・ 20653:Browser TVSDK Flash fallback werkt niet bij Win10 met de Update van Maker.</p> <p>・ Flash Fallback werkt met Flash Player versie 23 en hoger.</p> <p>・ 20087 - Chrome 59 Beta met</p> <p>Flash 25.0.0.171</p> <p>Bèta (standaard), werkt het afspelen HLS niet op de Flash Fallback-modus. Het werkt prima op de Canarische Eilanden.</p> </td> 
   <td><p>・ 12563: Streams met audiocodec mp4a.40.02 kunnen niet worden afgespeeld op Firefox vanwege een niet-ondersteunde audiocodec-tekenreeks in MPD. Audiocodec mp4a.40.2 wordt ondersteund.</p> <p>15029: Bij het schakelen tussen video's in multiView in UI-Kader, wordt de speel/pauzeknop niet dienovereenkomstig bijgewerkt.</p> <p>・ 16034:In Windows 8.1 IE leidt het aanroepen van reset() tot een onbekende MIME-typefout. Laad de media opnieuw om het afspelen te hervatten.</p> <p>・ 18235: Bepaalde zoekproblemen worden waargenomen bij DASH vod streams met Advertentie.</p> <p>・ 18727: Fout-API wordt niet ondersteund voor MSE</p> <p>18750: De gebeurtenissen van de Verandering van de status zouden in sommige gevallen voor zowel SDK als UI kader en in het Kader UI, kunnen de gebeurtenissen van IDLE en het Initialiseren StatusChange voor de gebeurtenisluisteraars missen die worden toegevoegd nadat het middel is geladen.</p> <p>・ 18889: Als de status MediaPlayer ERROR heeft, wordt het weergaveobject niet geretourneerd.</p> <p>・ 19039: Als AdobePSDK. MediaPlayer. seekToLocal() wordt gebruikt met een waarde groter dan EOF, en het afspelen begint bij MSE.</p> <p>・ 19049: Er wordt geen foutstatus gerapporteerd voor Flash Player op Chrome, IE en Firefox wanneer video tijdens het afspelen wordt geblokkeerd.</p> <p>・ 17.205: Het afspelen van video wordt gedurende enkele uren onderbroken tijdens het afspelen van niet-gedempte stream (Chromiumprobleem nr. 664033).</p> <p>・ 12308: Voor DASH-streams met composition_time_offset die zijn opgegeven, kan timeStampOffset zijn toegepast op de map in de Chrome-browser. Dit leidt tot een negatieve decoderingstijd en vandaar de fout MEDIA_ERR_ SRC_NOT_ SUPPORTED (Chromiumuitgave #398141).</p> <p>・ 14126: Het afspelen kan vastlopen op Firefox (issue# 1316024) vanwege de interne tussenruimte in de MSE-bronbuffer. Probeer te zoeken om het afspelen te hervatten.</p> <p>・ 19115: MS Edge en IE 11 (Win 8.1 en 10) stellen Oorsprong niet in op null bij omleiding naar CORS en mislukken toch omdat de header niet null is, wat leidt tot een afspeelfout.</p> <p>・ 19861:Probleem met gedrag bij toevoegen op bronbuffer voor media die al worden afgespeeld. Chrome verwerpt het toegevoegde fragment, inclusief VVV, waardoor een volgende decoderingsfout optreedt. (Chroomprobleem #735335)</p> <p>19921: Afspeelstallen voor bepaalde HLS-inhoud, ook al is de inhoud succesvol gebufferd (Chromiumuitgave #713540)</p> <p>・ 20444:Het zoeken naar het einde van het gebufferde bereik op IE en Edge kan ertoe leiden dat het afspelen vastloopt.</p> <p>・ 20511: Soms kan afwijzen door zoekopdrachten worden waargenomen bij HLS-streams met of zonder advertenties.</p> <p>・ 20743: In Windows 10 Chrome wordt de HLS Live-stream enkele seconden vóór het afspelen van de MP4-voorvertoning afgespeeld.</p> <p>・ 21043: De videodimensie is mogelijk niet correct bij de eerste belasting omdat er geen metagegevens beschikbaar zijn.</p> <p>・ 21115: Android-gebruikersbeweging is vereist om het afspelen te starten als een pre-roll-advertentie beschikbaar is voor video's in een afspeellijst.</p> <p>・ HLS Live ondersteunt de rollover van het tijdstempel niet.</p> <p>・ AAC-SSR-audio wordt niet ondersteund.</p> <p>Audiocodecs AC3 en Enhanced AC3 worden niet ondersteund.</p> <p>・ Voor stromen met timestamp discontinuïteit maar zonder discontinuïteitsmarkeringen</p> <p>・ Bij afspelen kunnen er litches en onjuist zoeken optreden door sprongen.</p> <p>・ De duur en de afspeelduur van de inhoud komen mogelijk niet overeen.</p> <p>・ discontinuaties tussen weergaven en uitvoeringen moeten overeenkomen met andere wijzen, wat kan leiden tot synchroniseren en problemen met vastlopen.</p> <p>・ Bijschriften en WebVTT worden mogelijk niet dicht bij het einde van de stream weergegeven.</p> <p>・ Wijzigingen in audiocodec worden niet ondersteund voor tijdstempelsprongen.</p> <p>・ Het invoegen van een advertentie wordt niet ondersteund.</p> <p>・ De modus Snel voorwaartse truc kan leiden tot een afspeellus in Win 8.1 IE 11 (MS-nummer #12446268).</p> <p>DASH:</p> <p>・ Voor live streams - liveprofiel met een dynamisch type wordt ondersteund.</p> <p>・ Voor VoD-streams - Live-profiel van het type static wordt ondersteund.</p> <p>Voor VoD-streams - vraagprofiel is niet gecertificeerd voor workflows voor advertenties.</p> </td> 
   <td><p>・ Live DASH en DASH Video on Demand-streams worden niet ondersteund.</p> <p>・ Het afspelen van PIP-video (Picture-in-Picture) wordt niet ondersteund op iOS in de modus Volledig scherm.</p> <p>Minder manifest voor extensie Safari (Video Tag) zonder juiste koptekst voor inhoudstype werkt niet.</p> </td> 
   <td><p>・ applicationID in de afzenderapp moet gelijk zijn aan de gegenereerde id bij het registreren van de URL van de ontvanger als een aangepaste ontvanger-app.</p> <p>・ De referentiespeler is gecertificeerd voor DASH-workflows. UI-framework is niet gecertificeerd.</p> <p>Raadpleeg <a href="https://developers.google.com/cast/docs/media"><em>hier</em></a> voor een lijst met ondersteunde mediacodecs.</p> </td> 
  </tr> 
  <tr> 
   <td>FER VOD</td> 
   <td>Algemeen afspelen (afspelen, pauzeren, zoeken)</td> 
   <td> </td> 
   <td>18098: Bepaalde zoekproblemen worden waargenomen bij HLS LBA FER-stroom.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Adaptieve bitsnelheid</td> 
   <td><p>・ 20079: Buffer herschrijven bij zoeken binnen gebufferd bereik.</p> <p>2008: Flash ABR-gedrag is in overeenstemming met MSE.</p> </td> 
   <td><p>・ De audio slechts fallback variant in een stroom ABR wordt genegeerd wegens buffer-gerelateerde beperkingen.</p> <p>・ 12289: ABR-besturingsparams zijn niet van toepassing op audio in het geval van ongedempte HLS/DASH-streams.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>608/708 Bijschriften</td> 
   <td> </td> 
   <td><p>・ 7810: Op Android 4.4.4 lijkt Chrome geen ondersteuning te hebben voor elementaire CSS-lettertypefamilies die door de speler worden gebruikt, zodat de functie voor het wijzigen van lettertypestijlen niet werkt.</p> <p>・ De CC-kanalen kunnen niet worden gewijzigd in het geval van 608 bijschriften.</p> <p>・ Geavanceerde opmaakfuncties worden niet ondersteund voor 608 bijschriften.</p> <p>Ingesloten bijschriften (608/708), die zijn gemarkeerd met de toegankelijkheidscode, worden ondersteund.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>WebVTT</td> 
   <td> </td> 
   <td><p>・ 5206: Gebiedstags in een WebVTT-bestand worden door de speler genegeerd bij het weergeven van de bijschriften.</p> <p>・ DASH: Fragmented /Segmented VTT-bestanden worden niet ondersteund.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Manifest failover</td> 
   <td>21056: Bij Flash Fallback treedt geen failover op voor Live stream als de primaire stream een fout van 404 retourneert tijdens het afspelen.</td> 
   <td>Manifest failover is alleen van toepassing op inhoud en niet op advertenties.</td> 
   <td>Het ontbreken van playlist failover werkt op Safari slechts voor de foutencode 404 van HTTP.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Geavanceerde failover</td> 
   <td> </td> 
   <td><p>・ Segmentfailover biedt geen ondersteuning voor het overslaan van niet-beschikbare segmenten en het verder afspelen.</p> <p>2053: Ontbrekende segmenten in een afspeellijst moeten worden behandeld als een Discontinuïteit en het afspelen moet worden hervat vanaf het volgende beschikbare segment.</p> <p>21267: De omschakeling van de stroom wegens over ontbreken kan tot download van oudere segmenten leiden.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>QoS- en Player-meldingen</td> 
   <td>21129: De framesnelheid is niet beschikbaar bij Flash fallback.</td> 
   <td><p>・ 11170:</p> <p>Timed_Event is niet beschikbaar voor Browser TVSDK met MSE in tegenstelling tot Browser TVSDK met Flash Fallback.</p> <p>21129: De framesnelheid wordt niet berekend voor live streams.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Ondersteuning voor Koekjeskoppen</td> 
   <td> </td> 
   <td> </td> 
   <td><p>De markering Credentials en cookie headers worden niet ondersteund in Safari.</p> <p>21051: Als u cookies wilt toestaan in Safari, schakelt u de instelling "Cookies and website data" in via Voorkeuren &gt; Privacy.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Aangepaste tags</td> 
   <td>14763: Aangepaste tags die niet beginnen met #, moeten niet worden ondersteund. Op dit moment wordt het object TimedMetadata gemaakt en gerapporteerd voor dergelijke tags tijdens de Flash Fallback.</td> 
   <td>Streams met inband aangepaste tags worden niet gecertificeerd.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Laatste inbindingsaudio</td> 
   <td> </td> 
   <td><p>・ Het invoegen van een advertentie wordt niet ondersteund voor HLS Live LBA-streams.</p> <p>・ 17273: HLS VOD LBA-streams schakelen over op standaarduitvoering in geval van failover en kunnen niet worden teruggezet naar de laatst geselecteerde versie.</p> <p>・ 20251: HLS Live LBA-stream blijft mogelijk op zoek.</p> <p>・ 20497: De speler blijft in bufferstatus als niet-gedempte HLS LBA-streams ontbrekende audio- of videoframes dichtbij het einde van de stream hebben.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>302 Omleiding</td> 
   <td> </td> 
   <td><p>15787: 302</p> <p>Redirect optimalisatie wordt niet ondersteund in Windows Edge- en IE-browsers, omdat deze de eigenschap responseURL in het XMLHttpRequest-object niet ondersteunen.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 17: Geavanceerde afspeelfuncties**

<table> 
 <tbody> 
  <tr> 
   <td>Inhoudstype</td> 
   <td>Functie</td> 
   <td>Flash</td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (alleen DASH-weergave)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Afspelen bij verschuiving</td> 
   <td><p>Het starten van het afspelen bij een bepaalde verschuivingswaarde wordt niet ondersteund in MP4-inhoud.</p> </td> 
   <td>20492: De middelste-rol advertenties voorafgaand aan de compensatie worden gespeeld alvorens de inhoud van de compensatiewaarde hervat.</td> 
   <td>Afspelen met verschuivingsfunctie wordt niet ondersteund op iOS.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Steen afspelen</td> 
   <td>Vloeiend afspelen werkt niet voor stromen zonder iFrame-uitvoeringen.</td> 
   <td><p>・ Trick Play-aanpassingen worden niet ondersteund in Firefox en Internet Explorer en daarom is de omgekeerde trustmodus niet beschikbaar in deze browsers.</p> <p>・ Trickplay is niet beschikbaar wanneer u inhoud samen met advertenties afspeelt.</p> <p>・ 10435: Tijdens het afspelen van DASH loopt de video vast bij voorwaartse truc in Internet Explorer (Win 8.1)</p> <p>met tussenpozen. Dit gebeurt omdat we de eigenschap playbackRate van de video-elementen gebruiken zonder de truc play-aanpassing.</p> <p>14182: Mogelijk wordt de gebeurtenis seek niet ontvangen tijdens het terugspoelen in Chrome en werkt de trustmodus daarom niet.</p> <p>・ 14942: U kunt afspeelsnelheden instellen op Chrome voor Android, zelfs in het geval van niet-truc-afspeelstreams, maar de instelling wordt niet toegepast en het afspelen wordt gewoon voortgezet.</p> <p>・ 17308: Seek werkt niet in de Trickplay-modus.</p> <p>・ 17309: In Chrome-browser kan de omgekeerde trustmodus niet langer dan 2 seconden worden gebruikt.</p> <p>19272: In geval van DASH-streams wordt het gebruik van trick-play mogelijk niet hersteld bij buffering in Windows 10 Edge-browser.</p> </td> 
   <td>De modus Terugspoelen wordt niet ondersteund.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>ID3-parsering</td> 
   <td>20346: De byte voor tekstcodering van ID3-frames moet ook worden geretourneerd door SDK.</td> 
   <td><p>ID3-tags die beschikbaar zijn in audiogegevenstransportstreams (ADTS), worden genegeerd door de SDK.</p> <p>・ 12378: Metagegevens met tijdslimiet voor ID3 worden op verschillende tijdstippen geparseerd op Flash en browser met ondersteuning voor MSE en daarom is het weergavegedrag op de tijdlijn van de verwijzingsspeler ook anders.</p> <p>・ 19247: ID3-parsering wordt niet ondersteund in UI-framework.</p> </td> 
   <td><p>・ 20323: PRIV ID3-tag die wordt gebruikt om de tijdstempel van het eerste sample van het aac-segment aan te geven, wordt niet geparseerd door Safari (Safari-uitgave #32422733)</p> <p>・ 20350: Op bepaalde apparaten (waaronder MAC OS X 10.1, iPad10) biedt Safari geen gebeurtenis voor het wijzigen van de actiepunten in de trustmodus en dus worden ID3-frames niet ontvangen. (Safari-uitgave #32450526)</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Ondersteuning van discontinue markeertekens</td> 
   <td> </td> 
   <td><p>・ Client-kant en invoeging wordt niet ondersteund met HLS-streams die discontinuïteit bevatten.</p> <p>・ Wijzigingen in audiocodec zijn niet toegestaan voor onderbrekingen in HLS-stroom.</p> <p>・ Audio Track-switch wordt niet ondersteund voor HLS-stream met discontinuïteitsmarkeringen</p> </td> 
   <td>Voor HLS-streams met discontinuïteit is het nummer van de discontinuïteitsvolgorde een vereiste voor het afspelen op Safari.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 18: Functies voor inhoudsbeveiliging**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhoudstype</strong></td> 
   <td><strong>Functie</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (alleen DASH-weergave)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>Bytebereik wordt niet ondersteund met gecodeerde AES-128-inhoud.</td> 
   <td>12324: Met HLS AES-128 gecodeerde streams kunnen niet worden afgespeeld op Safari als er geen IV-tag is opgegeven.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660: De HTML5-speler genereert een interne serverfout voor de verlopen PlayReady gecodeerde streepjesinhoud.</p> <p>・ 16720: DASH DRM-gecodeerde inhoud werkt niet als beginkenmerk in punt-tag ontbreekt.</p> <p>・ 18589: Afspelen wordt niet ondersteund voor DRM-beveiligde VoD-stream met meerdere Dash-perioden met Xlink.</p> <p>・ 18653: Het afspelen van de Inhoud van de Multiperiode van Widevine met Veelvoudige Toetsen, houdt bij eerste periode tegen en kan niet op volgende Periode schakelen.</p> <p>・ 18656: MultiPeriod Stream afspelen, gecodeerd met verschillende toetsen, wordt niet afgespeeld.</p> <p>Playready 2.0 for Dash is not certified.</p> <p> </p> <p> </p> </td> 
   <td>12602: HLS Fairplay DRM-metagegevens worden herhaaldelijk vernieuwd door de HTML5-speler op Safari</td> 
   <td><p>DASH Widevine DRM-inhoud die via Bento4 is verpakt, kan worden afgespeeld. Inhoud die is verpakt via Offline Packager en Shaka Packager, wordt niet afgespeeld. DASH PlayReady DRM wordt niet ondersteund.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 19: Core Ad Insertion-functies (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhoudstype</strong></td> 
   <td><strong>Functie</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (alleen DASH-weergave)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Pre/Mid/Post</td> 
   <td> </td> 
   <td><p>・ Prerolladvertenties met actieve HLS-inhoud worden in de modus Dual Player afgespeeld.</p> <p>・ DASH-advertenties met HLS-inhoud en HLS-advertenties met DASH-inhoud worden niet ondersteund.</p> <p>・ 19002: In HTML5 Player with MSE adBreak. insertType retourneert geen correcte waarde voor het juiste invoegtype, d.w.z. dat de client is ingevoegd en of de server is ingevoegd.</p> <p>7794: Op mobiele apparaten (iOS, Android met Chrome 33 of lager of de native browser) waar de standaardbesturingsbalk in de modus Volledig scherm zichtbaar is, zijn de knoppen seek en fast forward beschikbaar wanneer Advertentie afspelen.</p> <p>・ 11048: Het schakelen van ad naar HLS Live-inhoud verloopt niet vloeiend in het geval van extensies van mediabron.</p> <p>・ 16083: Op Android 4.4 Chrome v52 kan het gebeuren dat HLS en HLS-inhoud leiden tot een decoderingsfout in de pijplijn na het afspelen.</p> <p>・ 16097: Fouten die tijdens het afbreken van de advertentie zijn aangetroffen, worden mogelijk niet afgehandeld, waardoor de hoofdstream het afspelen kan stoppen.</p> <p>・ 18095: MP4-advertenties worden niet ondersteund met live HLS-inhoud.</p> <p>19120: Meerdere zoekopdrachten op HLS-advertenties met HLS-inhoud kunnen ertoe leiden dat de stream het afspelen stopt.</p> <p>・ 19131: De bufferbedekking kan verschijnen terwijl het schakelen van pre-rol en onderbreking aan inhoud.</p> <p>・ 20296: In het geval van HLS Live streams, kan het terugzoeken in DVR-venster gevolgd door het zoeken over opgeloste mid rolls leiden tot een afspeelval.</p> <p>・ 20298:HLS Live streams met halverwege rolletjes de eerste halverwege rol en beweegt zich uit het venster DVR.</p> <p>・ 20317: HLS Live-streams kunnen stagneren bij het schakelen naar volgende advertentie of van advertentie naar inhoud voor het geval dat een break meer dan één advertentie bevat.</p> 
    <ul> 
     <li>Advertenties in het DVR-venster van HLS Live streams worden niet opgelost.</li> 
    </ul> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2,0/3,0</td> 
   <td> </td> 
   <td>SDK neemt opeenvolgingsattributen binnen reactie VMAP voor VAST en Bron niet op.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2,0/3,0</td> 
   <td> </td> 
   <td>2079: De SDK neemt het reekskenmerk binnen de VMAP-reactie voor VAST en Source niet in acht.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VMAP 1.0</td> 
   <td> </td> 
   <td>12014: Het kenmerk VMAP repeat wordt niet ondersteund.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Creatieve herverpakking</td> 
   <td> </td> 
   <td>21464: De reactie van de advertentie wordt volledig genegeerd als het maken van een nieuw pakket mislukt voor een van de advertenties in het advertentiespoor.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 20: Geavanceerde Ad Insertion-functies (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Inhoudstype</strong></td> 
   <td><strong>Functie</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 in Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 in Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (alleen DASH-weergave)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Alleen advertentie</td> 
   <td> </td> 
   <td>20056: De eigenschap van de Player-technologie is niet relevant omdat deze is gebaseerd op de hoofdinhoud die leeg is in het geval van alleen-advertentie-afspelen</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Aangepast advertentiebeleid</td> 
   <td> </td> 
   <td><p>・ Advertentiepatronen worden niet ondersteund met MP4-advertenties en MP4-inhoud.</p> <p>・ 13973: Aangepaste advertenties - Het SKIP-beleid genereert geen complete-gebeurtenis bij gebruik met MSE.</p> <p>・ 14939: Aangepast beleid voor advertentieprestaties slaat over en slaat ad-break over, werkt niet voor DASH-inhoud.</p> <p>・ 17131: Het eerste frame van de advertentie is zichtbaar en de inhoud wordt dan hervat in het geval van het beleid voor SKIP en break.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Companion ads/banneradvertenties/Klikbare advertenties</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>Banneradvertenties zijn niet zichtbaar wanneer u de referentiespeler gebruikt.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・ Advertentiepatronen worden niet ondersteund voor VPAID-advertenties.</p> <p>・ 15032: VPAID-advertenties in combinatie met MP4- of HLS-advertenties in een ad-break worden niet ondersteund.</p> <p>・ 19001: Op Android en iOS zijn dubbele audiotracks hoorbaar wanneer VPAID-advertentie met MP4 wordt afgespeeld als hoofdinhoud, een van de hoofdinhoud en een van de advertenties.</p> <p>・ 20762: VPAID-advertenties worden niet ondersteund voor Beeld-in-beeld (PIP).</p> <p>・ 21172: De gebeurtenis Play complete wordt niet ontvangen voor HLS VOD-inhoud met VPAID-advertenties.</p> <p>・ 21173: onAdBreakCompleteEvent wordt niet ontvangen voor HLS VOD-inhoud en post roll VPAID-advertenties.</p> </td> 
   <td>De speler wisselt tussen normale wijze en volledig-schermwijze terwijl het schakelen tussen VPAID en Belangrijkste inhoud.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 21: Integraties**

| **Inhoudstype** | **Functie** | **Flash** | **HTML5 in Firefox, IE, Chrome, Android Chrome** | **HTML5 in Safari, iOS Safari** | **Chromecast (alleen DASH-weergave)** |
|---|---|---|---|---|---|
| VOD + Live | Adobe Analytics VHL-integratie |  | 19004: Het bijhouden van videoanalyses is niet beschikbaar via UI Configurator Tool. |  |  |

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).