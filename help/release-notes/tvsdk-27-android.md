---
title: Opmerkingen bij de release TVSDK 2.7 voor Android
seo-title: Opmerkingen bij de release TVSDK 2.7 voor Android
description: Opmerkingen bij de release van TVSDK 2.7 voor Android beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK Android 2.7
seo-description: Opmerkingen bij de release van TVSDK 2.7 voor Android beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK Android 2.7
uuid: 4013b97d-29f9-435b-8772-b19df7054282
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: bab78e9f-f9ba-4e1c-b778-0936ae704037
translation-type: tm+mt
source-git-commit: 9c6a6f0b5ecff78796e37daf9d7bdb9fa686ee0c
workflow-type: tm+mt
source-wordcount: '4123'
ht-degree: 0%

---


# Opmerkingen bij de release van TVSDK 2.7 voor Android {#tvsdk-for-android-release-notes}

Opmerkingen bij de release van TVSDK 2.7 voor Android beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK Android 2.7

## TVSDK Android 2.7 {#tvsdk-android}

De Android-referentiespeler wordt geleverd bij Android TVSDK in de map samples/directory van uw distributie. In het bijbehorende bestand README&lt;.md wordt uitgelegd hoe u de referentiespeler kunt maken.

>[!NOTE]
>
>Als u de referentiespeler wilt maken, zoals wordt beschreven in het bestand README.md dat met de release wordt gedistribueerd, moet u het volgende doen:
>
>1. Download VideoHeartbone.jar van [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) (VideoHeartbeat-bibliotheek voor Android v2.0.0)
>1. Extraheer VideoHeartbeat.jar naar de map libs/.

>



## Nieuwe functies {#new-features}

TVSDK 2.7 voor Android bevat alle functies van versie 1.4, behalve de functies die niet worden ondersteund in [Feature Matrix](#feature-matrix).

**Android TVSDK 2.7**

* **Ondersteuning voor parallelle ad-resolutie**

TVSDK 2.7 biedt ondersteuning voor de gelijktijdige oplossing van alle aanvragen voor Advertentie in een Advertentiereinde in plaats van sequentiële resolutie.

### Nieuwe functies in de vorige releases {#new-features-previous-releases}

**Versie 2.5.6**

* **TVSDK 2.5 ondersteunt Android P**
* **Achtergrondaudio inschakelen**

   Om het afspelen van audio in te schakelen wanneer de toepassing van de voorgrond naar de achtergrond wordt verplaatst, moet de toepassing de enableAudioPlaybackInBackground-API van MediaPlayer aanroepen met de waarde true als het argument wordt gebruikt wanneer de speler zich in de status PREPARED bevindt.

* **alwaysUseAudioOutputLatency(boolean val) in MediaPlayer-klasse**

Wanneer deze optie is ingesteld, gebruikt u uitvoerlatentie in de audiotijdstempelberekening.
Booleaanse parameters val - True gebruikt audiouitvoerlatentie voor audiotijdstempelberekening.

* **Geoptimaliseerd voor de beste afspeelervaring, zelfs als de bandbreedtesnelheid plotseling afneemt.**
TVSDK annuleert nu, indien nodig, het downloaden van het actieve segment en schakelt dynamisch over naar de juiste uitvoering. Dit wordt gedaan door naadloos tussen bitsnelheden zonder onderbrekingen te schakelen.

**Versie 2.5.5**

* **Gedeeltelijke invoeging van advertentie-einde**

   TV-achtige ervaring om mee te doen in het midden van een advertentie zonder de tracking te starten voor de gedeeltelijk bekeken advertentie.\
   Voorbeeld**: **De gebruiker sluit zich bij in het midden (bij 40 seconden) van een 90 seconde en onderbreking die uit drie 30 seconden bestaat. Dit is 10 seconden in de tweede advertentie in de pauze.
   * De tweede advertentie wordt afgespeeld gedurende de resterende duur (20 sec.), gevolgd door de derde advertentie.
   * Er worden geen trackers voor de gedeeltelijke advertentie geactiveerd (tweede advertentie). De trackers voor slechts de derde advertentie worden geactiveerd.

* **Beveiligd laden van advertentie via HTTPS**

   Adobe Primetime biedt een optie voor het aanvragen van een eerste aanroep naar primetime en server en CRS via https.

* **AdSystem en Creative ID toegevoegd aan CRS-aanvragen**

   * Nu &#39;AdSystem&#39; en &#39;CreativeId&#39; opnemen als nieuwe parameters in de verzoeken 1401 en 1403.

* **API setEncodeUrlForTracking in NetworkConfiguration-klasse** verwijderd als de onveilige tekens in een URL moeten worden gecodeerd.

**Versie 2.5.4**

Android TVSDK v2.5.4 biedt de volgende updates en API-wijzigingen:

* Veranderingen in standaardwaarde voor WebViewDebbuging
De WebViewDebbuging-waarde wordt geplaatst aan Vals door gebrek. Om het toe te laten, roep setWebContentsDebuggingEnabled (waar) in de toepassing.
* Upgrade van OpenSSL- en Curl-versie
Bijgewerkt libcurl naar v7.57.0 en OpenSSL naar v1.0.2k.
* Toegang op toepassingsniveau voor VAST-reactieobject
Introduceerde een nieuwe API NetworkAdInfo::getVastXml() die toegang van het VAST-reactieobject tot de toepassing biedt.

**Versie 2.5.3**

Android TVSDK v2.5.3 biedt de volgende updates en API-wijzigingen.

* Alle TVSDK-klanten die CRS gebruiken, worden aangeraden hun apps te upgraden met TVSDK 2.5.3.85 of hoger op Android. Dit is een vervolgkeuzelijst in plaats van de bestaande app-implementatie. Na de upgrade van TVSDK controleert u op de creatieve URL-aanvragen van CRS in een proxyprogramma (bijv. Charles) en bevestig dat de hostnaam en -versie in het pad overeenkomen met de URL-voorbeeldstructuur hieronder.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* De gebruikersagent van TVSDK kan worden aangepast: We hebben enkele nieuwe API&#39;s toegevoegd om de gebruikersagents aan te passen.

   * setCustomUserAgent(String-waarde)
   * getCustomUserAgent()

* Cookies delen tussen Android-toepassing en TVSDK: Android TVSDK ondersteunt nu de toegang tot cookies tussen de JAVA-laag (opgeslagen in CookieStore van de Android-toepassing) en de C++ TVSDK-laag. Nu, is het mogelijk om de koekjes in inheemse C++ laag te plaatsen en/of te wijzigen aangezien zij aan de Opslag van het Koekje van Java zullen worden blootgesteld.
* API-wijzigingen:

   * Er wordt een nieuwe Event CookiesUpdatedEvent toegevoegd. Het wordt verzonden door de mediaspeler wanneer het cookie wordt bijgewerkt.
   * Een nieuwe API wordt toegevoegd aan NetworkConfiguration::set/ getCustomUserAgent() om de aangepaste gebruikersagent te gebruiken.
   * Een nieuwe API wordt toegevoegd aan NetworkConfiguration::set/ getEncodedUrlForTracking om het coderen van Onveilige karakters te forceren.
   * Een nieuwe API wordt toegevoegd aan NetworkConfiguration::getNetworkDownVerificationUrl() om een URL voor netwerkverificatie in te stellen bij een failover.
   * Er wordt een nieuwe eigenschap toegevoegd aan TextFormat::treatSpaceAsAlphaNum die bepaalt of ruimte moet worden behandeld als alfanumeriek bij het weergeven van bijschriften.

* Wijzigingen in SizeAvailableEvent: Eerder werden getHeight()- en getWidth()-methoden van SizeAvailableEvent in 2.5.2 gebruikt om de framehoogte en -breedte te retourneren, die werden geretourneerd door de media-indeling. Nu worden uitvoerhoogte en uitvoerbreedte respectievelijk geretourneerd door decoder.
* Wijzigingen in buffergedrag: Het buffergedrag wordt gewijzigd. Het is aan ontwikkelaar van de Toepassing op wat zij in het geval van buffer leeg willen doen. 2.5.3 gebruikt de grootte van de spelbuffer bij buffer lege situatie.

**Versie 2.5.2**

Android TVSDK v2.5.2 biedt belangrijke foutoplossingen en enkele API-wijzigingen.

**Versie 1.5.1**

De belangrijke nieuwe functies die zijn uitgebracht in Android 2.5.1.

* **Prestatieverbeteringen** De nieuwe TVSDK 2.5.1-architectuur biedt een aantal prestatieverbeteringen. Gebaseerd op statistieken van een derdebenchmarkingsstudie, verstrekt de nieuwe architectuur een 5x vermindering van starttijd en 3.8x minder gelaten vallen kaders in vergelijking met het industriegemiddelde:

   * **Onmiddellijk aan voor VOD en levend -** Wanneer u onmiddellijk toelaat, initialiseert TVSDK en buffert media alvorens playback begint. Omdat u meerdere MediaPlayerItemLoader-instanties tegelijk op de achtergrond kunt starten, kunt u meerdere streams bufferen. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen op het nieuwe kanaal onmiddellijk gestart. TVSDK 2.5.1 biedt ook ondersteuning voor de streams Instant On voor **live**. De live streams worden opnieuw gebufferd wanneer het live venster wordt verplaatst.

      * **Verbeterde logica ABR -** De nieuwe logica ABR is gebaseerd op bufferlengte, snelheid van verandering van bufferlengte, en gemeten bandbreedte. Dit zorgt ervoor dat ABR het juiste beetjetarief kiest wanneer de bandbreedte fluctueert en ook het aantal tijden optimaliseert de bitsnelheidschakelaar eigenlijk door het tarief te controleren waarbij de bufferlengte verandert.
      * **Gedeeltelijk segment downloaden/subsegmentatie -** TVSDK verkleint de grootte van elk fragment verder, zodat het afspelen zo snel mogelijk kan worden gestart. Het fragment moet om de twee seconden een keyframe hebben.
      * **Lazy ad resolution -** TVSDK wacht niet op resolutie van niet pre-preroll advertenties alvorens playback te beginnen, zo verminderend de starttijd. API&#39;s zoals zoeken en spelen met truc zijn nog steeds niet toegestaan totdat alle advertenties zijn opgelost. Dit is van toepassing op VOD stromen die met CSAI worden gebruikt. Bewerkingen zoals zoeken en vooruitspoelen zijn niet toegestaan tot de advertentiesolutie is voltooid. Voor live streams kan deze functie niet worden ingeschakeld voor het corrigeren van advertenties tijdens een live gebeurtenis.
      * **Blijvende netwerkverbindingen - Met** deze functie kan TVSDK een interne lijst met permanente netwerkverbindingen maken en opslaan. Deze verbindingen worden opnieuw gebruikt voor veelvoudige verzoeken, eerder dan het openen van een nieuwe verbinding voor elk netwerkverzoek en dan het daarna vernietigen. Dit verhoogt de efficiëntie en verlaagt de latentie in de netwerkcode, wat resulteert in snellere afspeelprestaties.
Wanneer TVSDK een verbinding opent, vraagt het de server om een *keep-live* verbinding. Dit type verbinding wordt mogelijk niet door alle servers ondersteund. In dat geval wordt TVSDK opnieuw gebruikt voor het maken van een verbinding voor elk verzoek. Bovendien heeft TVSDK, terwijl permanente verbindingen standaard zijn ingeschakeld, nu een configuratieoptie zodat toepassingen de permanente verbindingen desgewenst kunnen uitschakelen.
      * **Parallelle download - Het** downloaden van video en audio parallel in plaats van in reeks vermindert opstartvertragingen. Met deze functie kunnen HLS Live- en VOD-bestanden worden afgespeeld, optimaliseert u het beschikbare bandbreedtegebruik van een server, vermindert u de kans dat u in situaties met bufferonderbreking terechtkomt en minimaliseert u de wachttijd tussen downloaden en afspelen.
      * **Parallel en gedownload -** TVSDK-prefetches worden parallel aan het afspelen van de inhoud geplaatst voordat de advertentie wordt afgebroken, zodat advertenties en inhoud naadloos kunnen worden afgespeeld.

* **Afspelen**

   * **MP4-inhoud afspelen -** MP4-korte clips hoeven niet opnieuw te worden getranscodeerd om te worden afgespeeld in TVSDK.
Opmerking: Het omschakelen van ABR, het spelen van een truc, en het opnemen, laat audioband, en sub-segmentatie worden niet gesteund voor MP4 playback.
   * **Trick play met adaptieve bitsnelheid (ABR) -** Met deze functie kan TVSDK schakelen tussen iFrame-streams in de truc-afspeelmodus. U kunt niet-iFrame-profielen gebruiken om met lagere snelheden te bedriegen.
   * **Vloeiende truckplay -** Deze verbeteringen verbeteren de gebruikerservaring:

          * Adaptieve bitsnelheid en framesnelheid selecteren tijdens het spelen van een truc, gebaseerd op bandbreedte- en bufferprofiel
          * Gebruik van de hoofdstream in plaats van de IDR-stream om tot 30 fps snel te worden afgespeeld.
      
* **Inhoud beschermen**

   * **Op resolutie gebaseerde uitvoerbeveiliging -** Deze functie koppelt afspeelbeperkingen aan specifieke resoluties en biedt fijnere korrelige DRM-besturingselementen.

* **Workflowondersteuning**

   * **Directe integratie van facturering -** Dit verzendt factureringsmetriek naar Adobe Analytics backend, die door Adobe Primetime voor stromen wordt verklaard die door de klant worden gebruikt.
TVSDK verzamelt automatisch meetgegevens, met inachtneming van het verkoopcontract van de klant, om periodieke gebruiksrapporten te genereren die voor factureringsdoeleinden worden vereist. Bij elke streamstartgebeurtenis gebruikt TVSDK de API voor het invoegen van Adobe Analytics-gegevens om factuurmetriek, zoals inhoudssoort, voor het invoegen ingeschakelde vlaggen en voor het drm ingeschakelde vlaggen - gebaseerd op de duur van de factureerbare stream - naar de Adobe Analytics Primetime-rapportsuite te verzenden. Dit heeft geen invloed op of wordt niet opgenomen in de eigen Adobe Analytics-rapportreeksen of serveraanroepen van de klant. Op verzoek wordt dit gebruiksrapport voor facturering periodiek naar klanten verzonden. Dit is de eerste fase van de factureringsfunctie die alleen gebruiksfacturering ondersteunt. Het kan worden gevormd gebaseerd op het verkoopcontract gebruikend APIs die in de documentatie worden beschreven. Deze functie is standaard ingeschakeld. Raadpleeg het voorbeeld voor de referentiespeler als u deze functie wilt uitschakelen.
   * **Verbeterde failover-ondersteuning -** Aanvullende strategieën die zijn geïmplementeerd om het afspelen zonder onderbreking voort te zetten, ondanks fouten met hostservers, afspeelbestanden en segmenten.

* **Reclame**

   * **Maat Integration -** Ondersteuning voor meting van de weergavemogelijkheden van advertenties vanuit Mat.
   * **Companion banners -** Companion banners worden naast een lineaire advertentie weergegeven en worden vaak ook na afloop van de advertentie weergegeven in de weergave. Deze banners kunnen van het type html (een HTML-fragment) of iframe (een URL naar een iframe-pagina) zijn.

* **Analyse**

   * **VHL 2.0 -** Dit is de recentste geoptimaliseerde Video Heartbeats Library (VHL) integratie voor automatische inzameling van gebruiksgegevens voor Adobe Analytics. De complexiteit van de API&#39;s is verminderd om de implementatie te vereenvoudigen. Download de VHL-bibliotheek [v2.0.0 voor Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) en extraheer het JAR-bestand in de map libs.

* **SizeAvailableEventListener**
   * getHeight() en getWidth() methoden van SizeAvailableEvent retourneren nu uitvoer in respectievelijk hoogte en breedte. De beeldverhouding kan als volgt worden berekend:

      ```
      SizeAvailableEvent e;
      
      DAR = e.getWidth()/ e.getHeight();
      
      Storage Aspect Ratio in terms of Sar width and Sar height can also be used to calculate Frame width and Frame height:
      
      SAR = e.getSarWidth()/e.getSarHeight();
      
      frameHeight = e.getHeight();
      
      frameWidth = e.getWidth()/SAR;    
      ```

* **Cookies**

   * Android TVSDK ondersteunt nu toegang tot JAVA-cookies die zijn opgeslagen in CookieStore van de Android-toepassing. Een callback API (onCookiesUpdated) wordt verstrekt om te registreren wanneer een nieuwe Koekje als deel van de &quot;reeks-Koekjeskopbal&quot;van de Reactie komt. Deze cookies zijn beschikbaar als een lijst met HttpCookie(s) die voor een ander URI/domein wordt gebruikt door deze cookie-waarden in te stellen op die specifieke URI/domein met gebruik van CookieStore. De cookie-waarden in TVSDK worden ook bijgewerkt met de CookieStore-API voor toevoegen.

## Eigenschappenmatrix {#feature-matrix}

TVSDK voor Android ondersteunt een aantal functies die u kunt implementeren om functionaliteit toe te voegen aan uw videotoepassingen.

In de onderstaande tabel met functies geeft een &#39;Y&#39; aan dat de functie wordt ondersteund in de huidige versie.

| Functie | Inhoudstype | HLS |
|---|---|---|
| Algemeen afspelen (Afspelen, Pauzeren, Zoeken) | VOD + Live | Y |
| FER - Algemeen afspelen (afspelen, pauzeren, zoeken) | FER VOD | Y |
| Zoeken wanneer een advertentie wordt afgespeeld | VOD + Live | Niet ondersteund |
| AC3 | VOD + Live | Niet ondersteund |
| MP3 | VOD | Niet ondersteund |
| MP4-inhoud afspelen | VOD | Y |
| Adaptive Bit Rate Switching Logic | VOD + Live | Y |
| Alleen audio afspelen | VOD + Live | Y |
| Ondersteuning voor meerdere CDN&#39;s | VOD + Live | Niet ondersteund |
| Afspelen van advertenties met media met alleen audio | VOD + Live | Niet ondersteund |
| Ondertiteling - 608/708 | VOD + Live | Y |
| Ondertiteling - WebVTT | VOD + Live | Y |
| Kennelijke failover | VOD + Live | Y |
| Geavanceerde failover | VOD + Live | Y |
| QoS- en spelersmeldingen | VOD + Live | Y |
| Ondersteuning voor cookie headers | VOD + Live | Y |
| Ondersteuning voor aangepaste HTTP-headers | VOD + Live | Y (aanbieding toestaan vereist) |
| Parameters voor bufferbesturing instellen | VOD + Live | Y |
| Aangepaste besturingselementen voor bitsnelheid instellen | VOD + Live | Y |
| Aangepaste manifest-tags | VOD + Live | Y |
| Te laat inbinden van audio | VOD + Live | Y |
| 302 Omleiding | VOD + Live | Y |
| Afspelen met verschuiving | VOD + Live | Y |
| Alleen audio afspelen | VOD + Live | Y |
| Steen afspelen | VOD + Live | Y |
| Langzame beweging in Steen afspelen | VOD + Live | Niet ondersteund |
| Vloeiend afspelen van steen (met ABR) | VOD + Live | Y |
| ID3-parsering | VOD + Live | Y |
| Zwart-out van advertenties | VOD + Live | Niet ondersteund |
| Direct aan | VOD + Live | Niet ondersteund |
| Ondersteuning van discontinue markeertekens | VOD + Live | Y |
| 302 Draairichting | VOD + Live | Y |

| Functie | Inhoudstype | HLS |
|---|---|---|
| Algemeen afspelen, advertenties ingeschakeld | VOD + Live | Y |
| FER-inhoud met ingeschakelde advertenties | VOD | Y |
| Standaardgedrag advertentie | VOD + Live | Y |
| VAST 2,0/3,0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| MP4-advertenties | VOD + Live | Y (van CRS) |
| Steen afspelen met advertenties ingeschakeld | VOD + Live | Y |
| Alleen advertentie | VOD | Y |
| Doelparameters | VOD + Live | Y |
| Aangepaste parameters | VOD + Live | Y |
| Aangepast gedrag voor advertentie | VOD + Live | Y |
| Aangepaste advertentietags | Live | Y |
| Aangepaste AD-oplossingen | VOD + Live | Y |
| Aangepaste en resolver van vrijloopwiel | VOD | Y |
| C3 | VOD + Live | Niet ondersteund |
| Lazy en oplossen | VOD | Y |
| Ondersteuning voor discontinue markeertekens - SSAI | VOD + Live | Y |
| Extra&#39;s, banneradvertenties en aanklikbare advertenties | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y (JS) |
| Vroege advertentie afsluiten | Live | Y |
| Op regels gebaseerde Creative Prioritization | VOD + Live | Y |
| CRS-regels | VOD + Live | Y |
| JSON Ad Resolver | VOD + Live | Niet ondersteund |
| Moatintegratie | VOD + Live | Y |

| Functie | Inhoudstype | HLS |
|---|---|---|
| AES-codering | VOD + Live | Y |
| Voorbeeld AES-codering | VOD + Live | Y |
| Vertogende stromen | VOD + Live | Y |
| DRM | VOD + Live | Alleen Primetime DRM (in de toekomst: Widevine) |
| Extern afspelen (RBOP) | VOD + Live | Alleen Primetime DRM |
| Licentie roteren | VOD + Live | Alleen Primetime DRM |
| Toetsrotatie | VOD + Live | Alleen Primetime DRM |

| Functie | Inhoudstype | HLS |
|---|---|---|
| Adobe Analytics VHL-integratie | VOD + Live | Y |
| Facturering | VOD + Live | Y |

## Opgeloste problemen {#resolved-issues}

Waar de resolutie met een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond, bijvoorbeeld ZD#xxxxx

**Android TVSDK 2.7**

Dit gedeelte bevat een overzicht van het probleem dat is opgelost in de release van TVSDK 2.7.

* ZD#37166 - Fout die vraag volgt wordt in brand gestoken zelfs wanneer de advertentie fijn wordt gespeeld.
* ZD#37134 - Verkeerde advertentie-id&#39;s worden geretourneerd, voor het geval dat een omvattende (3P) advertentie aanwezig is met meerdere advertenties in VMAP-respons.

**Android TVSDK 2.5.6**

* ZD #34992 - Taal is leeg in Closed Caption.
   * Probleem verholpen waarbij TVSDK #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS niet parseerde vanuit hoofdmanifest voor het ophalen van de gegevens van het bijschriftvak.
* ZD #35078 - Android P-validatie.
   * TVSDK 2.5.6 is gevalideerd met de nieuwste bètabuild(s) van Android P. Geen problemen gevonden vanwege het nieuwe Android-besturingssysteem.
* ZD #34149 - Player gaat door met verzoeken om manifests, zelfs als er een fout optreedt.
   * Het probleem waarbij TVSDK herhaalde oproepen deed, is opgelost, zelfs als alle profielen zijn ingedrukt (fout 404).
* ZD #31533 - Audio afspelen op Android nadat de app naar de achtergrond is verzonden.
   * Toegevoegde `enableAudioPlaybackInBackground` API van MediaPlayer die met &quot;Waar&quot;als argument (wanneer de speler in de VOORBEREIDENDE staat is) zou moeten worden geroepen om playback van audio toe te laten wanneer app op achtergrond is.

**Android TVSDK 2.5.5**

* ZD #21647 - Android TVSDK brengt 640x368 op de hoogte wanneer de werkelijke videogrootte 640x360 is.
   * Vanwege variabele m_nOutputHeight (in AndroidMCVideoDecoder) die wordt bijgewerkt met framehoogte in plaats van de werkelijke uitvoerhoogte. Belangrijke wijzigingen aangebracht in de functie getVideoFrame om m_nOutputHeight correct te berekenen.
* ZD #26614 - Urgent — derde partij, dienst doen/programmatic — not serve impressions.
   * Verbeterde eerdere correctie door het gebruik van hoofdletters en kleine letters bij XML-parsering waarbij het probleem reproduceerbaar was wanneer &quot;space&quot; voor het &quot;equal&quot;-teken staat, zoals &lt;VAST version =&quot;2.0&quot;>
* ZD #29296 - Android: Voeg AdSystem en Creative id toe aan CRS-aanvragen.
   * Nu &#39;AdSystem&#39; en &#39;CreativeId&#39; opnemen als nieuwe parameters in de verzoeken 1401 en 1403.
* ZD #33062 - TVSDK crasht bij het voorkomen van pipe-tekens in VAST-respons onder CDATA-knooppunt
   * API setEncodeUrlForTracking in NetworkConfiguration-klasse verwijderd als de onveilige tekens in een te coderen URL.
* ZD #33063 - CRS dossier selectielogica werd gebroken - TVSDK verzond geen CRS- verzoek om Webformaat maar verzond het voor 3gpp- dossiers.
   * De logica is nu opgelost. Als u mediabestanden gebruikt in de webindeling en de 3gpp-indeling, wordt een CRS-verzoek verzonden voor webpagina. En als u beide mediabestanden gebruikt met de indeling 3gpp, wordt de CRS-aanvraag verzonden voor het hoogste bitsnelheids-3gpp-bestand.
* ZD #33125 - De Android-toepassing loopt vast met een specifieke DoubleClick-tag in de VMAP.
   * Correctie van het scenario om het neerstorten te vermijden.
* ZD #32256 - Licentie roteren en belangrijke rotatieprobleem - Adobe Access.
   * Probleem verholpen met de initialisatie van segmenten met de DRM-metagegevens voor SampleAES-inhoud. Werkt prima met AES128-inhoud.
* ZD #33619 - snel-door:sturen een groeiende playlist inhoud die in als buffer optredende voor staat dichtbij levend punt wordt geplakt.
   * Behandelde de zaak wanneer het oversteken van het live punt in de truc-afspeelmodus.
* ZD #34151 - Objecten met getimede metagegevens zijn niet in orde.
   * Twee TimedMetadata-gebeurtenissen werden in willekeurige volgorde weergegeven als ze tot hetzelfde tijdstip in de tijdlijn behoorden. De oorspronkelijke volgorde werd in manifest gehandhaafd.
* ZD #34189 - Probleem bij het begin van een advertentie-einde.
   * Het probleem was met SSAI-advertenties die met discontinuïteit verbonden zijn. De oorzaak was een gedrag als we aan het begin van dergelijke advertenties zoeken naar een hoofdframe en dat vinden we niet. De reden was dat de minimale audio-tijdstempel van de advertentie vóór de minimale video-tijdstempel lag. Daarom zoeken we uiteindelijk naar een keyframe bij een onjuist fragmentDump-gegevens. Nu opgelost.
* ZD #34528 - Videoresolutie niet hoger dan 640x360 op FireTV-dongle.
   * Verbeterde oplossing voor de nieuwste firmware-updates.
* ZD #34793 - TVSDK 2.5.x gebruikte om met douane inhoudoplosser in sommige gevallen te crashen wanneer VideoEngine veronderstelde dat auditudeSettings beschikbaar zijn en zij niet waren.
   * De crash vond plaats als gevolg van een functieaanroep op een Null gezamenlijke aanwijzer (auditudeSettings). Er is een voorwaardelijke controle toegevoegd in VideoEngineTimeline::placeToSourceTimeline() om te controleren of auditudeSettings beschikbaar zijn voordat iets op dat object wordt aangeroepen.
* ZD #32584 - Geen toegang tot volledige informatie aanwezig in de &lt;Extensions> knoop van een VAST reactie.
   * Probleem met XML-parsering is opgelost. NetworkAdInfo biedt nu alle informatie die aanwezig is in het knooppunt &lt;Extensions>.
* ZD #35086 - Geen volledige extensiegegevens van de speler krijgen in het geval van specifieke VMAP-reacties.
   * Het probleem was specifiek voor extensie xml omdat XML-parsering niet werkte als extension xml dubbele aanhalingstekens binnen de kenmerkwaarde had. Probleem opgelost.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Afspeelsessie die foutopsporing op afstand in de webweergave mogelijk maakt.
   * WebViewDebbuging wordt geplaatst aan Vals door gebrek. Als u foutopsporing wilt inschakelen, stelt u true in via de toepassing met setWebContentsDebuggingEnabled (true).
* ZenDesk#33011 - Tijdlijn voor toevoegen wordt niet opgelost in het geval van een mislukte CRS-aanvraag.
   * Wanneer een CRS-aanvraag voor een advertentie mislukt, wordt de tijdlijn opgelost en worden de resterende advertenties afgespeeld.
* ZenDesk#34528 - Videoresolutie werkt niet verder dan 640x360 op FireTV-dongle van de derde generatie.
   * De videoresolutie schakelt omhoog als schakelaars van de beetjetarief.
* ZenDesk#33192 - AudioTrack heeft een null-naam wanneer een track wordt opgehaald via AudioUpdatedEventListener::onAudioUpdated.
   * In een paar scenario&#39;s op Vuurtelevisie, werd de gebeurtenis onAudioUpdate in brand gestoken wanneer er geen daadwerkelijke audio update was. Dit is nu opgelost.

**Android TVSDK 2.5.3**

* Zendesk#32216 - Abonnement op aangepaste TimedMetadata-tags werkt niet.
   * We retourneren ID3-gegevens als een bytearray (ter ondersteuning van APIC- of generieke gegevens) naar de client, terwijl in 1.4 de retourreeks wordt geretourneerd. Byte-array kan geen null-teken met een einde verwerken. De array gaf daarom een speciaal teken voor de client weer. Dit probleem is nu opgelost.
* Zendesk#32670 - Player kan niet worden overgeslagen naar overbodige afspeellijst
   * Dit werkt nu prima en setNetworkDownVerificationUrl werkt zoals verwacht.
* Zendesk#32369 - Gesloten bijschrift geeft verschillende kleurdetails en artefacten weer.
   * Het probleem met CC-glitches is opgelost in de meest recente build
* Zendesk#25590 - Verbeteren: TVSDK-cookie-opslag (C++ naar JAVA)
   * Android TVSDK ondersteunt nu de toegang tot cookies tussen de JAVA-laag (opgeslagen in CookieStore van de Android-toepassing) en de C++ TVSDK-laag.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 lijkt niet de oplossing voor PTPLAY-20269 te hebben
Dit probleem is opgelost en geïntegreerd in 2.5.2 vertakking.
* Zendesk#31806 - Auditude sticks in PREPARING
De speler bleef vastzitten in de voorbereidingsstatus omdat response xml een lege tag had. Het probleem is nu opgelost.
* Zendesk#31727 - TVSDK 2.5-tekens voor gesloten bijschriften worden verwijderd of verkeerd gespeld.
   * Het probleem is opgelost en we zetten geen tekens neer of spelfouten op.
* Zendesk#31485 - DrmManager in 2.5
   * Er is een probleem opgetreden bij het maken van DRMManager via nieuwe DRMManager (context). Geïmplementeerde DRMService-klasse die DRMManager zou verschaffen.
* Zendesk#32794- 1080P-resolutiestream die niet wordt afgespeeld op Android.
   * We hebben SizeAvailableEvent en eerder getHeight() en getWidth() methoden van SizeAvailableEvent in 2.5 gewijzigd. Deze werden gebruikt om Framehoogte en framebreedte te retourneren, die werden geretourneerd door de media-indeling. De uitvoerhoogte en uitvoerbreedte worden nu respectievelijk door de decoder geretourneerd.
* Zendesk #19359 Flash Player loopt vast vanwege de positie van het kenmerk #EXT-X-FAXS-CM in manifest op setniveau.
   * De tag #EXT-X-FAXS-CM moet altijd op de bovenste afspeellijst worden weergegeven voordat afzonderlijke bitsnelheden of segmenten in de afspeellijst worden weergegeven.

**Android TVSDK 2.5.2**

* Zendesk#17305 Artefacten in gesloten bijschriften met een niet-dekkende achtergrond.
De eigenschap setTreatSpaceAsAlphaNum in TextFormat wordt weergegeven. Standaard is de eigenschap False. Stel de eigenschap in op Waar in een client om het probleem met de donkere ruimte op te lossen.

* De weergave Zendesk#25097 CC bevat visuele artefacten met CC-instellingen.
De eigenschap setTreatSpaceAsAlphaNum in TextFormat wordt weergegeven. Standaard is de eigenschap False. Stel de eigenschap in op Waar in een client om het probleem met de donkere ruimte op te lossen.

* De tekenreeks Zendesk #31620 User Agent die vervalt uit de TVSDK-speler, is afgebroken.
De userAgent-tekenreeks wordt niet meer afgebroken na 128 tekens.
Adobe Primetime version string wordt toegevoegd aan de system user agent.

* Zendesk #30809 Ontbrekende SEEK_END-gebeurtenis voorkomt dat de app overgaat naar een afspeelstatus.
* Zendesk #30415 Closed Caption&#39;s &#39;Cyan&#39;-kleur is nu een donkerdere kleurtoon van blauw (turquoise) in vergelijking met de vorige Primetime TVSDK-releases.

   De kleur wordt veranderd van DarkCyan in Cyan.

* Zendesk #30727 VOD-advertenties worden niet gedownload/opgelost.

   Als er in VMAP XML een lege VAST markering zonder een expliciete sluitende markering (&quot;&lt;/VAST>&quot;) en zonder een nieuw lijnkarakter na het is, dan wordt VMAP XML niet behoorlijk geparseerd en de advertenties kunnen niet spelen.

**Android TVSDK 2.5.1**

* Apparaatspecifiek vastlopen (Samsung Galaxy Tab 4); VOD DRM LBA met Auditude en klik op advertenties.
* VHL - de Onjuiste hartslagvraag wordt verzonden wanneer het beginnen van inhoud van een compensatie.
* Wanneer VPAID-advertenties worden afgespeeld, roept de VHL-hartslag om gebeurtenis:type:play aan en ontbreken deze.
* Nadat de speler de status COMPLETE heeft gekregen, gaat hij terug naar de status PLAYING met SKIP en BreakPolicy voor postroll-advertenties.
* Cookies worden niet gekoppeld aan uitgaande en callbacks.
* Advertentiepunten zijn niet zichtbaar.
* HLS met afzonderlijke EAC3 SAP-track worden niet geladen.
* De speler crasht terwijl TVSDK een Scherm op intent ontvangt nadat de Media Player is hersteld.

## Bekende problemen en beperkingen {#known-issues-and-limitations}

**Android TVSDK 2.7**

* TVSDK 2.7 biedt ondersteuning voor gelijktijdige resolutie van maximaal 5 Ads.
* In het geval van VMAP-respons gaan Ad-aanroepen in één advertentieeinde tegelijkertijd en worden de pagina-einden opeenvolgend opgelost.
* In het geval van FER, worden de vraag van de Advertentie in elke kans opgelost gelijktijdig.

### Bekende problemen en beperkingen in de vorige releases{#known-issues-limitations-previous-releases}

**Android TVSDK 2.5.6**

* Meerdere VMAP-opnamen en afbrekingen worden niet ondersteund.

**Android TVSDK 2.5.3**

Deze versie heeft de volgende problemen:

* Bij het afspelen van live video kunnen er problemen optreden bij het synchroniseren van audio en video op eenvoudige apparaten of bij slechte netwerkomstandigheden.
* Voor FER stromen, kunnen virtualTime en localTime verschillen. Ook FER met offset werkt niet.
* Het afspelen kan vastlopen wanneer de optie late inbinding van audio-inhoud wordt gezocht.
* WebVTT-bijschriften kunnen soms niet meer synchroon zijn voor LIVE-inhoud.
* Het afspelen van een paar frames kan periodiek worden bekeken nadat het frame uit een ad-einde is gekomen.
* Soms wordt een fout van 303 gegenereerd voor Drievoudige wrapper ad-einden, ook al worden advertenties afgespeeld.

**Android TVSDK 2.5.2**

Deze versie heeft de volgende problemen:

* Het afspelen van live video kan problemen met audio- en videosynchronisatie hebben op eenvoudige apparaten.
* Het afspelen kan op momenten stagneren wanneer wordt gezocht naar het einde van de VOD-media.
* Voor FER stromen, kunnen virtualTime en localTime verschillen. FER met verschuiving werkt ook niet.

**Android TVSDK 2.5.1**

Deze versie van TVSDK heeft de volgende problemen:

* Bij het afspelen van live video kunnen er problemen optreden met het synchroniseren van audio en video op eenvoudige apparaten.
* Voor FER stromen, kunnen virtualTime en localTime verschillen. FER met verschuiving werkt ook niet.
* Als er in VMAP XML een lege VAST-tag is zonder een expliciete afsluitende tag (&lt;/VAST>) en zonder een nieuwe regel erna, wordt de VMAP XML niet correct geparseerd en worden advertenties mogelijk niet afgespeeld.
* VPAID post-roll wordt niet gesteund.

## Nuttige bronnen {#helpful-resources}

* [Systeemvereisten](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-2-7-for-android/overview/c-psdk-android-2_7-requirements.html)
* [TVSDK 2.7 voor Android-programmeergids](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-2-7-for-android/overview/c-psdk-android-2_7-overview-prod-audience-guide.html)
* [TVSDK Android Javadoc voor API-naslaggids](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html)
* [TVSDK Android C++ API Document](https://help.adobe.com/en_US/primetime/api/psdk/cpp/namespaces.html)  - Elke Java-klasse heeft een corresponderende C++-klasse en de C++-documentatie bevat meer verklarend materiaal dan de JavaDocs. Raadpleeg daarom de C++-documentatie voor een beter begrip van de Java API.
* [TVSDK 1.4 tot 2.5 voor migratiehandleiding voor Android (Java)](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* Zie het `Application_Changes_for_Screen_On_Off.pdf`-bestand dat is opgenomen in de build voor informatie over het afhandelen van scenario&#39;s voor het in- en uitschakelen van schermen.
* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).