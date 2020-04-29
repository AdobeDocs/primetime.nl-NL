---
title: Opmerkingen bij de release TVSDK 3.11 voor Android
seo-title: Opmerkingen bij de release TVSDK 3.11 voor Android
description: De opmerkingen bij de release TVSDK 3.11 voor Android beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK Android 3.11
seo-description: De opmerkingen bij de release TVSDK 3.11 voor Android beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK Android 3.11
uuid: 685d46f5-5a02-4741-af5c-91e91babd6f7
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 3a27379f-3cef-4ea3-bcae-21382dc1e9fd
translation-type: tm+mt
source-git-commit: fdb4e4eb741dd066017d96205cea8cbd15dcbc7b

---


# Opmerkingen bij de release TVSDK 3.11 voor Android {#tvsdk-for-android-release-notes}

In de Release-notities van TVSDK 3.11 voor Android wordt beschreven wat nieuw of gewijzigd is, welke problemen zijn opgelost en welke problemen bekend zijn en wat de apparaatproblemen zijn in TVSDK Android 3.11.

De Android-referentiespeler wordt geleverd bij Android TVSDK in de map samples/directory van uw distributie. In het bijbehorende bestand README.md wordt uitgelegd hoe u de referentiespeler kunt maken.

>[!NOTE]
>
>Als u de referentiespeler wilt maken, zoals wordt beschreven in het bestand README.md dat met de release wordt gedistribueerd, moet u het volgende doen:
>
>1. Download VideoHeartbone.jar van [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) (VideoHeartbeat-bibliotheek voor Android v2.0.0)
>1. Extraheer VideoHeartbeat.jar naar de map libs/.
>



TVSDK voor Android biedt veel prestatieverbeteringen ten opzichte van eerdere versies. Het biedt een hoogwaardige kijkervaring en beschikt over alle functies van versie 1.4, met uitzondering van de ondersteuning voor Multi-CDN.

De uitgebreide reeks functies die wordt ondersteund en niet wordt ondersteund, wordt weergegeven in de sectie Matrix [met](#feature-matrix) functies van de opmerkingen bij de release.

## Android TVSDK 3.11

**Ophalen van vak voor beveiligingssysteemspecifieke koptekst (PSSH) is toegestaan**

TVSDK staat nu het halen van het Systeem-Specifieke Kopdoos van de Bescherming toe verbonden aan huidige geladen Middel van Media. Nieuwe API `getPSSH()` is toegevoegd aan `com.adobe.mediacore.drm.DRMManager`.
Zie [Widevine DRM](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md)voor meer informatie.

De belangrijkste problemen die in de huidige release zijn opgelost, worden vermeld in de sectie [Opgeloste problemen](#resolved-issues) .

### Nieuwe en verbeterde functies in de vorige versies

**Android TVSDK 3.10**

Deze release was gericht op het oplossen van problemen met klanten zoals vermeld in de [sectie Opgeloste problemen](#resolved-issues) .

**Android TVSDK 3.9**

* **Beveiligde levering via HTTPS** - Android TVSDK 3.9 introduceert de veilige leveringsmogelijkheden via HTTPS om inhoud veilig te leveren met ongeëvenaarde schaal en prestaties.

   Om veilige levering via HTTPS mogelijk te maken, wordt nieuwe API in de `NetworkConfiguration` klasse geïntroduceerd.

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **Ondersteuning voor pre-rol met gedeeltelijke ad-break-functie** - Dankzij deze verbetering biedt TVSDK 3.8 ondersteuning voor pre-roll-advertenties met PABI (Partial Ad-Break feature).

   De pre-roll advertentie, indien beschikbaar, wordt gespeeld, en dan speelt de inhoud van het levende punt geëmuleerd de ervaring van levende televisie.

**Android TVSDK 3.7**

* Voor Widevine-testinhoud kan een nieuwe API `setMediaDrmCallback` in de DRMManager-klasse de standaardimplementatie van de MediaDRmCallback-interface overschrijven.

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* Correctie van AppCrash-fout voor niet-afhandeling `MediaPlayerEvent.ITEM_UPDATED` in C++-laag (Android 64-bits).

**Android TVSDK 3.6**

* **Verbeter uw apps voor de vereiste** 64-bits functionaliteit - De native bibliotheek `(libAVEAndroid.so)` wordt nu bijgewerkt en beschikbaar gesteld in twee versies. Bestaande native bibliotheeklocatie (32 bits) van armeabi is gewijzigd en een extra arm64-v8a (64 bits)-bibliotheek is geïntroduceerd in `/framework/Player to /framework/Player/armeabi``/framework/Player/arm64-v8a.`

**Versie 3.5**

* **Even in tijd en resolutie** - TVSDK 3.5 verwijdert de ondersteuning van de afgespeelde advertenties uit de tijdlijn.
* **Ondersteuning ingeschakeld voor offline afspelen** - Met offline afspelen kunnen gebruikers nu video-inhoud downloaden naar hun apparaten en deze bekijken wanneer ze geen verbinding hebben. Raadpleeg &quot;[Offline afspelen met Android](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf)&quot; voor meer informatie.

**Versie 3.4**

* TVSDK ondersteunt nu het afspelen van CMAF-streams voor CBC-gecodeerde en platte streams.

**Versie 3.3**

* **API-wijzigingen**

   * Er wordt een nieuwe API toegevoegd `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` voor de afhandeling van netwerkfouten en -onderbrekingen.
      * waarbij n) het aantal pogingen is.

**Versie 3.2**

* **Parallelle ad Resolution and Manifest download support**

   * TVSDK 3.2 ondersteunt de gelijktijdige resolutie in plaats van de sequentiële resolutie voor alle verzoeken om advertentie en pagina-einden, behalve voor VMAP.

   * Alle advertenties in een advertentie-einde worden tegelijkertijd gedownload.

* **Ondersteuning ingeschakeld voor Ad Resolution en Manifest Download Timeout.**

   * Gebruikers kunnen nu de time-outwaarde instellen voor algemene ad-resolutie en duidelijke downloads.  In het geval van VMAP is de time-outwaarde van toepassing op afzonderlijke advertentieonderbrekingen, aangezien alle ad-einden opeenvolgend worden opgelost.

* **Nieuwe API&#39;s geïntroduceerd in de klasse AdvertisingMetadata:**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **Verwijderd onder API&#39;s uit de klasse AdvertisingMetadata:**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **Het afspelen van streams met AC3/EAC3-audiocodec is ingeschakeld**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` in `MediaPlayer` klasse

* **TVSDK ondersteunt CMAF en het afspelen van normale streams voor gecodeerde Windows CTR.**

* **Het afspelen van HEVC-streams van 4.000 pagina&#39;s wordt nu ondersteund.**

* **Parallel en vraag verzoeken** - TVSDK prefetst nu 20 en vraagverzoeken parallel.

**Versie 3.0**

* **TVSDK 3.0 biedt ondersteuning voor HEVC-streams (High Efficiency Video Coding).**

* **Even in tijd - Als u advertenties dichter bij de opmaakmarkeringen** Lazy Ad oplost, worden deze nu afzonderlijk opgelost. Eerder was de resolutie een tweefasenaanpak: De pre-rollen werden opgelost voorafgaand aan playbackbegin en alle midden/postrolgroeven gecombineerd nadat het spelen begon. Met deze verbeterde functie wordt elk ad-einde nu opgelost op een specifiek tijdstip vóór het ad-cuepunt.

> [!NOTE]
>
> Het luie Oplossen van Advertenties is nu veranderd om door gebrek worden uitgezet, en uitdrukkelijk moet worden toegelaten.

Er wordt een nieuwe API toegevoegd `AdvertisingMetadata::setDelayAdLoadingTolerance` om de vertraagde laadtolerantie voor deze advertentiemetagegevens te verkrijgen.\
Zoeken is nu toegestaan direct na het voorbereiden, en als u op ad-hocpauzes zoekt, wordt dit onmiddellijk opgelost voordat het zoeken is voltooid.\
De signaalmodi `SERVER_MAP` en `MANIFEST_CUES` worden ondersteund.

Zie [TVSDK 3.0 voor de Android-programmeergids](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) over API- en gebeurteniswijzigingen voor meer informatie.

* **Bijgewerkt`targetSdkVersion`tot laatste versie**

Bijgewerkt `targetSdkVersion` van 19 naar 27 voor een vloeiende werking.

* **Placement.Type getPlacementType() is nu een methode op interface TimelineMarker**

   Deze methode retourneert een plaatsingstype van Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL of Placement.Type.POST_ROLL. Als een advertentie-einde niet wordt opgelost, zal de getDuration () methode op de interface TimelineMarker 0 terugkeren.

**Versie 2.5.6.**

* **TVSDK 2.5 ondersteunt Android P.**

* **Achtergrondaudio inschakelen**

   Als u het afspelen van audio wilt inschakelen wanneer de toepassing van de voorgrond naar de achtergrond gaat, moet de toepassing de API van MediaPlayer aanroepen met de waarde true als het argument wanneer de speler zich in de status PREPARED bevindt. `enableAudioPlaybackInBackground`

* **alwaysUseAudioOutputLatency(boolean val) in MediaPlayer-klasse**

Wanneer deze optie is ingesteld, gebruikt u uitvoerlatentie in de audiotijdstempelberekening.
Booleaanse parameters val - True gebruikt audiouitvoerlatentie voor audiotijdstempelberekening.

* **Geoptimaliseerd voor de beste afspeelervaring, zelfs als de bandbreedtesnelheid plotseling afneemt**

TVSDK annuleert nu, indien nodig, het downloaden van het actieve segment en schakelt dynamisch over naar de juiste uitvoering. Dit wordt gedaan door naadloos tussen bitsnelheden zonder onderbrekingen te schakelen.

**Versie 2.5.5**

* **Gedeeltelijke invoeging van advertentie-einde**

   TV-achtige ervaring om mee te doen in het midden van een advertentie zonder de tracking te starten voor de gedeeltelijk bekeken advertentie.\
   Voorbeeld: De gebruiker verbindt zich in het midden (bij 40 seconden) van een 90 seconde en onderbreking die uit drie 30 seconden bestaat. Dit is 10 seconden in de tweede advertentie in de pauze.

   * De tweede advertentie wordt afgespeeld gedurende de resterende duur (20 sec.), gevolgd door de derde advertentie.

   * Er worden geen trackers voor de gedeeltelijke advertentie geactiveerd (tweede advertentie). De trackers voor slechts de derde advertentie worden geactiveerd.

* **Beveiligd laden van advertentie via HTTPS**

   Adobe Primetime biedt een optie waarmee u een eerste oproep naar primetime en server en CRS via https kunt uitvoeren.

* **AdSystem en Creative ID toegevoegd aan CRS-aanvragen**

   Nu worden de 1401- en 1403-verzoeken aangevuld `AdSystem` en `CreativeId` als nieuwe parameters.

* **API setEncodeUrlForTracking in NetworkConfiguration-klasse verwijderd** omdat de onveilige tekens in een URL moeten worden gecodeerd.

**Versie 2.5.4**

Android TVSDK v2.5.4 biedt de volgende updates en API-wijzigingen:

* Wijzigingen in de standaardwaarde voor `WebViewDebbuging`

   `WebViewDebbuging` waarde is standaard ingesteld op `Fals`e. Roep de toepassing aan om deze in te schakelen. `setWebContentsDebuggingEnabled(true)`

* **Upgrade van OpenSSL- en Curl-versie**

   Bijgewerkt libcurl naar v7.57.0 en OpenSSL naar v1.0.2k.

* Toegang op toepassingsniveau voor VAST-reactieobject

   Introduceerde een nieuwe API `NetworkAdInfo::getVastXml()` die toegang van het VAST reactievoorwerp tot de toepassing verleent.

**Versie 2.5.3**

Android TVSDK v2.5.3 biedt de volgende updates en API-wijzigingen.

* Alle TVSDK-klanten die CRS gebruiken, worden aangeraden hun apps te upgraden met TVSDK 2.5.3.85 of hoger op Android. Dit is een vervolgkeuzelijst in plaats van de bestaande app-implementatie. Na de upgrade van TVSDK controleert u op de creatieve URL-aanvragen van CRS in een proxyprogramma (bijv. Charles) en bevestig dat de hostnaam en -versie in het pad overeenkomen met de URL-voorbeeldstructuur hieronder.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* De gebruikersagent van TVSDK kan worden aangepast: We hebben enkele nieuwe API&#39;s toegevoegd om de gebruikersagents aan te passen.

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* Cookies delen tussen Android-toepassing en TVSDK: Android TVSDK ondersteunt nu de toegang tot cookies tussen de JAVA-laag (opgeslagen in CookieStore van de Android-toepassing) en de C++ TVSDK-laag. Nu, is het mogelijk om de koekjes in inheemse C++ laag te plaatsen en/of te wijzigen aangezien zij aan de Opslag van het Koekje van Java zullen worden blootgesteld.

* API-wijzigingen:

   * Er `CookiesUpdatedEvent` wordt een nieuwe gebeurtenis toegevoegd. Het wordt verzonden door de mediaspeler wanneer het cookie wordt bijgewerkt.

   * Er wordt een nieuwe API toegevoegd `NetworkConfiguration::set/ getCustomUserAgent()` om de aangepaste gebruikersagent te gebruiken.

   * Er wordt een nieuwe API toegevoegd om de codering van onveilige tekens te forceren. `NetworkConfiguration::set/ getEncodedUrlForTracking`

   * Er wordt een nieuwe API toegevoegd `NetworkConfiguration::getNetworkDownVerificationUrl()` om een URL voor netwerkverificatie in te stellen bij een failover.

   * Er wordt een nieuwe eigenschap toegevoegd `TextFormat::treatSpaceAsAlphaNum` die bepaalt of ruimte alfanumeriek moet zijn bij het weergeven van bijschriften.

* Wijzigingen in `SizeAvailableEvent`. Eerder, `getHeight()` en `getWidth()` methodes van `SizeAvailableEvent` in 2.5.2 gebruikt om de hoogte en kaderbreedte van het Kader terug te keren, die door media formaat werd teruggegeven. Nu worden uitvoerhoogte en uitvoerbreedte respectievelijk geretourneerd door decoder.

* Wijzigingen in buffergedrag: Het buffergedrag wordt gewijzigd. Het is aan ontwikkelaar van de Toepassing op wat zij in het geval van buffer leeg willen doen. 2.5.3 gebruikt de grootte van de spelbuffer bij buffer lege situatie.

**Versie 2.5.2**

Android TVSDK v2.5.2 biedt belangrijke foutoplossingen en enkele API-wijzigingen.

**Versie 2.5.1**

De belangrijke nieuwe functies die zijn uitgebracht in Android 2.5.1.

* **Prestatieverbeteringen -** De nieuwe TVSDK 2.5.1-architectuur biedt een aantal prestatieverbeteringen. Gebaseerd op statistieken van een derdebenchmarkingsstudie, verstrekt de nieuwe architectuur een 5x vermindering van starttijd en 3.8x minder gelaten vallen kaders in vergelijking met het industriegemiddelde:

* **Instant on for VOD en live -** Wanneer u instant on inschakelt, initialiseert de TVSDK en buffert deze media voordat het afspelen wordt gestart. Omdat u meerdere MediaPlayerItemLoader-instanties tegelijk op de achtergrond kunt starten, kunt u meerdere streams bufferen. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen op het nieuwe kanaal onmiddellijk gestart. TVSDK 2.5.1 ondersteunt ook Instant On voor **live** streams. De live streams worden opnieuw gebufferd wanneer het live venster wordt verplaatst.

* **Verbeterde logica ABR -** De nieuwe logica ABR is gebaseerd op bufferlengte, snelheid van verandering van bufferlengte, en gemeten bandbreedte. Dit zorgt ervoor dat ABR het juiste beetjetarief kiest wanneer de bandbreedte fluctueert en ook het aantal tijden optimaliseert de bitsnelheidschakelaar eigenlijk door het tarief te controleren waarbij de bufferlengte verandert.

* **Gedeeltelijk segment downloaden/subsegmentatie -** TVSDK verkleint de grootte van elk fragment verder, zodat het afspelen zo snel mogelijk kan worden gestart. Het fragment moet om de twee seconden een keyframe hebben.

* **Lazy en resolutie -** TVSDK wacht niet op het oplossen van niet-preroll advertenties voordat het afspelen wordt gestart, waardoor de opstarttijd afneemt. API&#39;s zoals zoeken en spelen met truc zijn nog steeds niet toegestaan totdat alle advertenties zijn opgelost. Dit is van toepassing op VOD stromen die met CSAI worden gebruikt. Bewerkingen zoals zoeken en vooruitspoelen zijn niet toegestaan tot de advertentiesolutie is voltooid. Voor live streams kan deze functie niet worden ingeschakeld voor het corrigeren van advertenties tijdens een live gebeurtenis.

* **Blijvende netwerkverbindingen -** Met deze functie kan TVSDK een interne lijst met permanente netwerkverbindingen maken en opslaan. Deze verbindingen worden opnieuw gebruikt voor veelvoudige verzoeken, eerder dan het openen van een nieuwe verbinding voor elk netwerkverzoek en dan het daarna vernietigen. Dit verhoogt de efficiëntie en verlaagt de latentie in de netwerkcode, wat resulteert in snellere afspeelprestaties.
Wanneer TVSDK een verbinding opent, vraagt het de server om een *levend* verbinding. Dit type verbinding wordt mogelijk niet door alle servers ondersteund. In dat geval wordt TVSDK opnieuw gebruikt voor het maken van een verbinding voor elk verzoek. Bovendien heeft TVSDK, terwijl permanente verbindingen standaard zijn ingeschakeld, nu een configuratieoptie zodat toepassingen de permanente verbindingen desgewenst kunnen uitschakelen.

* **Parallelle download: het** gelijktijdig downloaden van video en audio in plaats van in serie vermindert de opstartvertraging. Met deze functie kunnen HLS Live- en VOD-bestanden worden afgespeeld, optimaliseert u het beschikbare bandbreedtegebruik van een server, vermindert u de kans dat u in situaties met bufferonderbreking terechtkomt en minimaliseert u de wachttijd tussen downloaden en afspelen.

* **Parallel en gedownload—** TVSDK prefetches adverteren parallel aan het afspelen van de inhoud voordat de advertentie wordt afgebroken, zodat advertenties en inhoud naadloos kunnen worden afgespeeld.

* **Afspelen**

* **MP4-inhoud afspelen -** korte MP4-clips hoeven niet opnieuw te worden getranscodeerd om te worden afgespeeld in TVSDK.

   > [!NOTE]
   >
   > Het omschakelen van ABR, het spelen van een truc, en het opnemen, laat audioband, en sub-segmentatie worden niet gesteund voor MP4 playback.

* **Trick play met adaptieve bitsnelheid (ABR) -** Met deze functie kan TVSDK schakelen tussen iFrame-streams in de truc-afspeelmodus. U kunt niet-iFrame-profielen gebruiken om met lagere snelheden te bedriegen.

* **Vloeiende truckplay -** Deze verbeteringen verbeteren de gebruikerservaring:

   * Aangepaste bitsnelheid en framesnelheid selecteren tijdens het spelen van een truc, op basis van bandbreedte- en bufferprofiel

   * Gebruik van de hoofdstream in plaats van de IDR-stream om tot 30 fps snel te kunnen afspelen.

* **Inhoud beschermen**

   * **Op resolutie gebaseerde uitvoerbeveiliging -** Deze functie koppelt afspeelbeperkingen aan specifieke resoluties en biedt fijnere korrelige DRM-besturingselementen.

* **Workflowondersteuning**

   * **Integratie van directe facturering -** hiermee worden gegevens over facturering naar de achtergrond van Adobe Analytics verzonden, die door Adobe Primetime is gecertificeerd voor streams die door de klant worden gebruikt.
   TVSDK verzamelt automatisch metriek, met inachtneming van het klantenverkoopcontract om periodieke gebruiksrapporten te produceren die voor factureringsdoeleinden worden vereist. Bij elke streamstartgebeurtenis gebruikt TVSDK de API voor het invoegen van Adobe Analytics-gegevens om factuurmetriek, zoals het inhoudstype, en voor het invoegen ingeschakelde markeringen en (op basis van de duur van de factureerbare stream) drm-markeringen naar de Primetime-rapportsuite van Adobe Analytics te verzenden. Dit heeft geen invloed op of wordt niet opgenomen in de eigen Adobe Analytics-rapportreeksen of serveraanroepen van de klant. Op verzoek wordt dit gebruiksrapport voor facturering periodiek naar klanten verzonden. Dit is de eerste fase van de factureringsfunctie die alleen gebruiksfacturering ondersteunt. Het kan worden gevormd gebaseerd op het verkoopcontract gebruikend APIs die in de documentatie worden beschreven. Deze functie is standaard ingeschakeld. Raadpleeg het voorbeeld voor de referentiespeler als u deze functie wilt uitschakelen.

   * **Verbeterde failover-ondersteuning -** Aanvullende strategieën die zijn geïmplementeerd om het afspelen zonder onderbreking voort te zetten, ondanks fouten van hostservers, afspeelbestanden en segmenten.


* **Reclame**

   * **Moat Integration -** Ondersteuning voor meting van de weergavemogelijkheden van advertenties vanuit Mat.

   * **Companion banners -** Companion banners worden naast een lineaire advertentie weergegeven en worden vaak ook na afloop van de advertentie weergegeven in de weergave. Deze banners kunnen van het type html (een HTML-fragment) of iframe (een URL naar een iframe-pagina) zijn.

* **Analyse**

   * **VHL 2.0 -** Dit is de nieuwste geoptimaliseerde VHL-integratie (Video Heartbeats Library) voor automatische verzameling van gebruiksgegevens voor Adobe Analytics. De complexiteit van de API&#39;s is verminderd om de implementatie te vereenvoudigen. Download de VHL-bibliotheek [v2.0.0 voor Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) en extraheer het JAR-bestand in de map libs.

* **SizeAvailableEventListener**

   * `getHeight()` en `getWidth()` methoden of `SizeAvailableEvent` retourneert nu uitvoer in hoogte en breedte. De beeldverhouding kan als volgt worden berekend:

      ```java
      SizeAvailableEvent e;
      DAR = e.getWidth()/ e.getHeight();
      ```

      Opslagverhouding in termen van tekenbreedte en -hoogte kan ook worden gebruikt om de framebreedte en -hoogte te berekenen:

      ```java
      SAR = e.getSarWidth()/e.getSarHeight();
      frameHeight = e.getHeight();
      frameWidth = e.getWidth()/SAR;
      ```

* **Cookies**

   * Android TVSDK ondersteunt nu toegang tot JAVA-cookies die zijn opgeslagen in CookieStore van de Android-toepassing. Een callback API (onCookiesUpdated) wordt verstrekt om te registreren wanneer een nieuwe Koekje als deel van **reeks-Koekjesantwoordkopbal** komt. Deze cookies zijn beschikbaar als een lijst met HttpCookie(s) die voor een ander URI/domein wordt gebruikt door deze cookie-waarden in te stellen op die specifieke URI/domein met gebruik van CookieStore. De cookie-waarden in TVSDK worden ook bijgewerkt met de CookieStore-API voor toevoegen.

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
| Ondersteuning voor aangepaste HTTP-headers | VOD + Live | Y (Whitelisting vereist) |
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

Wanneer de resolutie aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond, bijvoorbeeld ZD#xxxxx.

**Android TVSDK 3.11**

Deze sectie bevat een overzicht van het probleem dat is opgelost in TVSDK 3.11 Android-release.

* ZD#41252 - Koreaanse tekens in WebVTT afgebroken na Android 7.1.

### Opgeloste problemen in de vorige releases

**Android TVSDK 3.10**

* ZD#40340 - De toepassing loopt vast met de fout &quot;App niet reageert&quot; bij het proberen van het afspelen nadat alle TS-bestanden (TypeScript) zijn gesplitst.

**Android TVSDK 3.8**

* Geen nieuwe uitgaven toegevoegd.

**Android TVSDK 3.7**

* Geen nieuwe uitgaven toegevoegd.

**Android TVSDK 3.6**

* Geen nieuwe uitgaven toegevoegd.

**Versie 3.5**

* ZD#37503 - JSON-reacties voor de CRS-regels worden in cache geplaatst om dubbele aanvragen te voorkomen.

**Versie 3.4**

* ZD#37996 - Oplossing voor een probleem met hap-afspeelproblemen bij lineaire en VOD CMAF HEVC-streams.
* ZD#37706 - Probleem met uitgestelde bijschriften is opgelost.
* ZD#37622 - Oplossing voor een probleem met fatale URISyntaxErrors voor specifieke advertenties.
* ZD#36938 - Oplossing voor een probleem met bitsnelheidsomschakeling naar de middelste bitsnelheid en vervolgens oppakken naar de hoogste bitsnelheid na het afsluiten van een truc.

**Versie 3.3**

* ZD#37394 - CMAF-element snel voorwaarts veroorzaakt artefacten na snelheidswijzigingen.
   * Probleem verholpen dat optreedt met een profielwijziging tijdens truc.
* ZD#37396 - Gebeurtenissen voor het bijhouden van advertenties ontbreken voor sommige mid-rolls en post-rolls.
   * Oplossing voor een specifiek probleem met gebeurtenissen voor het bijhouden van advertenties.
* ZD#37491 - HTTP-statuscode met foutmeta is niet aanwezig.
   * Werkt bij het verspreiden van netwerkfouten hoger in de stapel.
* ZD#37808 - Nieuwe aangepaste koptekst whelist.
   * Ondersteuning voor SSAI_TAG toegevoegd als onderdeel van deze correctie.
* ZD#37622 - URISyntax-fouten uit specifieke advertentiepods.
   * Probleem verholpen waarbij het afspelen van streams vastliep wanneer de Android-app van de klant advertenties aanbiedt met een niet-gecodeerd %
* ZD#37631 - Master manifest retry mechanism for Android TVSDK.
   * Nieuwe API in de netwerkconfiguratie voor de behandeling van deze verbetering toegevoegd. Als deze API niet wordt gebruikt, wordt manifest niet opnieuw geprobeerd. Als het dan wordt gebruikt zal manifest voor de behandeling van netwerkfouten en onderbrekingen opnieuw worden geprobeerd.

**Versie 3.2**

* ZD#37493- Tekenreeksspatiëring voor live afspelen wordt niet periodiek geactiveerd voor de eerste advertentie in de juiste volgorde.
* ZD#36985- Tekenreeksbakens worden niet verzonden voor lege en onderbrekingen in de VMAP-reactie.
* ZD#37134 - TVSDK genereert tijdelijk de verkeerde ID voor VMAP-respons.

**Versie 3.0**

* ZD#33740 - TVSDK genereert een onnodige waarschuwing vlak na het maken van een MediaPlayer-object en het aanroepen van replaceCurrentResource()

   * De eerdere correctie is verbeterd doordat alleen terugzetten wordt aangeroepen wanneer de speler is onderbroken

* ZD#36442 - Elke nieuwe playback verbreekt verbinding verre het zuiveren zitting die het onmogelijk maken om te zuiveren.

   * Foutopsporing is standaard niet mogelijk in de webweergave, omdat foutopsporing standaard niet is ingeschakeld. De toepassing moet foutopsporing inschakelen indien dit is vereist door het aanroepen van setWebContentsDebuggingEnabled(true) op een object dat is geretourneerd van MediaPlayer.getCustomAdView().

* ZD#33688 - Ondersteuning voor just-in-time en oplossing

   * Ad-einden worden met een opgegeven interval opgelost vóór de positie van het ad-einde.

* ZD#36441 - De duur van het livevenster neemt steeds meer dan 5 minuten in beslag, waardoor meerdere problemen ontstaan.

   * Probleem verholpen waarbij VirtualStartTime tweemaal werd toegevoegd tijdens het berekenen van het virtuele live-punt dat tot deze kwestie leidde.

**Android TVSDK 2.5.6**

* ZD #34992 - Taal is leeg in Closed Caption.

   * Probleem verholpen waarbij TVSDK #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS niet parseerde vanuit hoofdmanifest voor het ophalen van de details van de bijschrifttrack.

* ZD #35078 - Android P-validatie.

   * TVSDK 2.5.6 is gevalideerd met de nieuwste bètabuild(s) van Android P. Geen problemen gevonden vanwege het nieuwe Android-besturingssysteem.

* ZD #34149 - Player gaat door met verzoeken om manifests, zelfs als er een fout optreedt.

   * Het probleem waarbij TVSDK herhaalde oproepen deed, is opgelost, zelfs als alle profielen zijn ingedrukt (fout 404).

* ZD #31533 - Audio afspelen op Android nadat de app naar de achtergrond is verzonden.

   * Toegevoegde `enableAudioPlaybackInBackground` API van MediaPlayer die met &#39;True&#39; als argument (als speler zich in de status PREPARED bevindt) moet worden aangeroepen om het afspelen van audio mogelijk te maken wanneer de toepassing op de achtergrond wordt uitgevoerd.

**Android TVSDK 2.5.5**

* ZD #21647 - Android TVSDK brengt 640x368 op de hoogte wanneer de werkelijke videogrootte 640x360 is.

   * Vanwege variabele m_nOutputHeight (in AndroidMCVideoDecoder) die wordt bijgewerkt met framehoogte in plaats van de werkelijke uitvoerhoogte. Belangrijke wijzigingen aangebracht in de functie getVideoFrame om m_nOutputHeight correct te berekenen.

* ZD #26614 - Urgent — derde partij, dienst doen/programmatic — not serve impressions.

   * Verbeterde eerdere correctie door het gebruik van hoofdletters en kleine letters bij XML-parsering waarbij het probleem reproduceerbaar was wanneer &quot;space&quot; voor het &quot;equal&quot;-teken staat, zoals &lt;VAST version =&quot;2.0&quot;>

* ZD #29296 - Android: Voeg AdSystem en Creative id toe aan CRS-aanvragen.

   * Nu &#39;AdSystem&#39; en &#39;CreativeId&#39; opnemen als nieuwe parameters in de verzoeken 1401 en 1403.

* ZD #33062 - TVSDK crasht bij het voorkomen van pipe-tekens in VAST-respons onder CDATA-knooppunt

   * API setEncodeUrlForTracking in NetworkConfiguration-klasse verwijderd als de onveilige tekens in een te coderen URL

* ZD #33063 - CRS dossier selectielogica werd gebroken - TVSDK verzond geen CRS- verzoek om Webformaat maar verzond het voor 3gpp- dossiers.

   * De logica is nu opgelost. Als u mediabestanden gebruikt in de webindeling en de 3gpp-indeling, wordt een CRS-verzoek verzonden voor webpagina. En als u beide mediabestanden gebruikt met de indeling 3gpp, wordt de CRS-aanvraag verzonden voor het hoogste bitsnelheids-3gpp-bestand.

* ZD #33125 - De Android-toepassing loopt vast met een specifieke DoubleClick-tag in de VMAP.

   * Correctie van het scenario om het neerstorten te vermijden.

* ZD #32256 - probleem met licentiering en keyrotatie - Adobe Access

   * Probleem verholpen met de initialisatie van segmenten met de DRM-metagegevens voor SampleAES-inhoud. Werkt prima met AES128-inhoud.

* ZD #33619 - snel-door:sturen een groeiende playlist inhoud die in als buffer optredende voor staat dichtbij levend punt wordt geplakt.

   * Behandelde de zaak wanneer het oversteken van het levende punt in truc speelwijze

* ZD #34151 - Objecten met getimede metagegevens zijn niet in orde.

   * Twee TimedMetadata-gebeurtenissen werden in willekeurige volgorde weergegeven als ze tot hetzelfde tijdstip in de tijdlijn behoorden. De oorspronkelijke volgorde werd in manifest gehandhaafd.

* ZD #34189 - Probleem bij het begin van een advertentie-einde.

   * Het probleem was met SSAI-advertenties die met discontinuïteit verbonden zijn. De oorzaak was een gedrag als we aan het begin van dergelijke advertenties zoeken naar een hoofdframe en dat vinden we niet. De reden was dat de minimale audio-tijdstempel van de advertentie vóór de minimale video-tijdstempel lag. Daarom zoeken we uiteindelijk naar een keyframe bij een onjuist fragmentDump-gegevens. Nu opgelost.

* ZD #34528 - Videoresolutie niet hoger dan 640x360 op FireTV-dongle.

   * Verbeterde oplossing voor de nieuwste firmware-updates

* ZD #34793 - TVSDK 2.5.x gebruikte om met douane inhoudoplosser in sommige gevallen te crashen wanneer VideoEngine veronderstelde dat auditudeSettings beschikbaar zijn en zij niet waren.

   * De crash vond plaats als gevolg van een functieaanroep op een Null gezamenlijke aanwijzer (auditudeSettings). Er is een voorwaardelijke controle toegevoegd in VideoEngineTimeline::placeToSourceTimeline() om te controleren of auditudeSettings beschikbaar zijn voordat iets op dat object wordt aangeroepen.

* ZD #32584 - Geen toegang tot volledige informatie aanwezig in de &lt;Extensions> knoop van een VAST reactie.

   * Het probleem bij XML-parsering is opgelost en NetworkAdInfo biedt nu alle informatie die aanwezig is in het knooppunt &lt;Extensions>.

* ZD #35086 - Geen volledige extensiegegevens van de speler krijgen in het geval van specifieke VMAP-reacties.

   * Het probleem was specifiek voor extensie xml omdat XML-parsering niet werkte als extension xml dubbele aanhalingstekens binnen de kenmerkwaarde had. Probleem opgelost.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Afspeelsessie die foutopsporing op afstand in de webweergave mogelijk maakt.

WebViewDebbuging wordt geplaatst aan Vals door gebrek. Als u foutopsporing wilt inschakelen, stelt u true in via de toepassing met setWebContentsDebuggingEnabled (true).

* ZenDesk#33011 - Tijdlijn voor toevoegen wordt niet opgelost in het geval van een mislukte CRS-aanvraag.

   Wanneer een CRS-aanvraag voor een advertentie mislukt, wordt de tijdlijn opgelost en worden de resterende advertenties afgespeeld.

* ZenDesk#34528 - Videoresolutie werkt niet verder dan 640x360 op FireTV-dongle van de derde generatie.

   De videoresolutie schakelt omhoog als schakelaars van de beetjetarief.

* ZenDesk#33192 - AudioTrack heeft een null-naam wanneer een track wordt opgehaald via AudioUpdatedEventListener::onAudioUpdated.

   In een paar scenario&#39;s op Vuurtelevisie, werd de gebeurtenis onAudioUpdate in brand gestoken wanneer er geen daadwerkelijke audio update was. Dit is nu opgelost.

**Android TVSDK 2.5.3**

* Zendesk#32216 - Abonnement op aangepaste TimedMetadata-tags werkt niet.

   We retourneren ID3-gegevens als een bytearray (ter ondersteuning van APIC- of generieke gegevens) naar de client, terwijl in 1.4 de retourreeks wordt geretourneerd. Byte-array kan geen null-teken met een einde verwerken. De array gaf daarom een speciaal teken voor de client weer. Dit probleem is nu opgelost.
* Zendesk#32670 - Player kan niet worden overgeslagen naar overbodige afspeellijst

   Dit werkt nu prima en setNetworkDownVerificationUrl werkt zoals verwacht.
* Zendesk#32369 - Gesloten bijschrift geeft verschillende kleurdetails en artefacten weer.

   Het probleem met CC-glitches is opgelost in de meest recente build
* Zendesk#25590 - Verbeteren: TVSDK-cookie-opslag ( C++ tot JAVA )

   Android TVSDK ondersteunt nu de toegang tot cookies tussen de JAVA-laag (opgeslagen in CookieStore van de Android-toepassing) en de C++ TVSDK-laag.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 lijkt niet de oplossing voor PTPLAY-20269 te hebben

   Dit probleem is opgelost en geïntegreerd in 2.5.2 vertakking.
* Zendesk#31806 - Auditude sticks in PREPARING

   De speler bleef vastzitten in de voorbereidingsstatus omdat response xml een lege tag had. Het probleem is nu opgelost.
* Zendesk#31727 - TVSDK 2.5-tekens voor gesloten bijschriften worden verwijderd of verkeerd gespeld.

   Het probleem is opgelost en we zetten geen tekens neer of spelfouten op.
* Zendesk#31485 - DrmManager in 2.5

   Er is een probleem opgetreden bij het maken van DRMManager via nieuwe DRMManager (context). Geïmplementeerde DRMService-klasse die DRMManager zou verschaffen.
* Zendesk#32794- 1080P-resolutiestream die niet wordt afgespeeld op Android

   We hebben SizeAvailableEvent en eerder getHeight() en getWidth() methoden van SizeAvailableEvent in 2.5 gewijzigd. Deze werden gebruikt om Framehoogte en framebreedte te retourneren, die werden geretourneerd door media-indeling. De uitvoerhoogte en uitvoerbreedte worden nu respectievelijk door de decoder geretourneerd.
* Zendesk #19359 Flash Player loopt vast vanwege de positie van het kenmerk #EXT-X-FAXS-CM in manifest op setniveau.

   De tag #EXT-X-FAXS-CM moet altijd op de bovenste afspeellijst worden weergegeven voordat afzonderlijke bitsnelheden of segmenten in de afspeellijst worden weergegeven.

**Android TVSDK 2.5.2**

* Zendesk#17305 Artefacten in gesloten bijschriften met een niet-dekkende achtergrond.

   De eigenschap setTreatSpaceAsAlphaNum in TextFormat wordt weergegeven. Standaard is de eigenschap False. Stel de eigenschap in op Waar in een client om het probleem met de donkere ruimte op te lossen.

* De weergave Zendesk#25097 CC bevat visuele artefacten met CC-instellingen.

   De eigenschap setTreatSpaceAsAlphaNum in TextFormat wordt weergegeven. Standaard is de eigenschap False. Stel de eigenschap in op Waar in een client om het probleem met de donkere ruimte op te lossen.

* De tekenreeks Zendesk #31620 User Agent die vervalt uit de TVSDK-speler, is afgebroken.

   De userAgent-tekenreeks wordt niet meer afgebroken na 128 tekens.

   De Adobe Primetime-versietekenreeks wordt toegevoegd aan de gebruikersagent van het systeem.

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

**Android TVSDK 3.11**

* Geen nieuwe beperkingen toegevoegd.

### Bekende problemen en beperkingen in de vorige versies

**Android TVSDK 3.10**

* Geen nieuwe beperkingen toegevoegd.

**Android TVSDK 3.8**

* Geen nieuwe beperkingen toegevoegd.

**Android TVSDK 3.7**

* Geen nieuwe beperkingen toegevoegd.

**Android TVSDK 3.6**

* Geen nieuwe beperkingen toegevoegd.

**Android TVSDK 3.5**

* Geen nieuwe beperking toegevoegd.

**Android TVSDK 3.4**

* ID3, Closed Captions, Late Binding Audio Support is niet geverifieerd voor de CMAF-stream (CBC).
* Op sommige apparaten is er een probleem met een lage reproduceerbaarheid, waardoor videovervorming op de voorgrond kan optreden tijdens het spelen van truc op CMAF-streams.

**Android TVSDK 3.3**

* clip:c608-bijschriften worden niet ondersteund voor afspelen van CMAF-stroom.

**Android TVSDK 3.2**

* TVSDK 3.2 biedt geen ondersteuning voor het afspelen van CMAF Sample AES- en AES128-streams.
* CMAF-streams van HEVC bieden geen ondersteuning voor het afspelen van ondertitels.
* De groene kleur verschijnt voor WV Gecodeerde stromen wanneer het zoeken rond het niet-gecodeerde segment wordt uitgevoerd.
* CMAF-streams ondersteunen geen ID3-gebeurtenissen.
* HLS-streams bieden geen ondersteuning voor de indeling voor HTML-bijschriften.

**Android TVSDK 3.0**

* HEVC-ondersteuning heeft de volgende beperkingen in deze release

   * DRM wordt niet ondersteund
   * Ondersteuning voor CC (CEA 608/708) is niet geverifieerd
   * 4K-ondersteuning is nog niet aanwezig
   * Ondersteuning van ID3-tags is niet geverifieerd

* Voor gebeurtenissen voor advertentievoortgang weerspiegelt de tijdlijnbalk mogelijk niet de 100% nauwkeurige en afspeeltijd. Als tussenoplossing kunt u de voltooiing van het afspelen van de advertentie en de gebruikersinterface voor verschillende doeleinden kennen, zoals het bijwerken van de tijdlijnbalk, het verwijderen van en verwante gebruikersinterface, enz. `adcompleteevent`
* Vast en de vraag die van VMAP is teruggekeerd respecteert niet de just-in-Time lookahead positie.

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

* Bij het afspelen van live video kunnen er problemen optreden bij het synchroniseren van audio en video op eenvoudige apparaten.
* Voor FER stromen, kunnen virtualTime en localTime verschillen. FER met verschuiving werkt ook niet.
* Als er in VMAP XML een lege VAST-tag is zonder een expliciete afsluitende tag (&lt;/VAST>) en zonder een nieuwe regel erna, wordt de VMAP XML niet correct geparseerd en worden advertenties mogelijk niet afgespeeld.
* VPAID post-roll wordt niet gesteund.

## Nuttige bronnen {#helpful-resources}

* [Systeemvereisten](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-requirements.html)
* [TVSDK 3.10 voor Android-programmeergids](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-overview-prod-audience-guide.html)
* [TVSDK Android Javadoc voor API-naslaggids](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [TVSDK Android C++ API-document](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) - Elke Java-klasse heeft een corresponderende C++-klasse en de C++-documentatie bevat meer verklarend materiaal dan de JavaDocs. Raadpleeg daarom de C++-documentatie voor een beter begrip van de Java API.
* [TVSDK 1.4 tot 2.5 voor migratiehandleiding voor Android (Java)](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* Zie het `Application_Changes_for_Screen_On_Off.pdf` bestand dat is opgenomen in de build voor informatie over het afhandelen van schermscenario&#39;s aan/uit.
* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html) .
