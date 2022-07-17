---
title: TVSDK 3.13 voor opmerkingen bij de release van iOS
description: TVSDK 3.13 voor iOS Release-notities beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK iOS 3.13.
exl-id: adf8ab23-86d6-4113-b243-2709d5f7f829
source-git-commit: 59ea8008c828f3bdf275fea5cc2a59c37b0c4845
workflow-type: tm+mt
source-wordcount: '7575'
ht-degree: 0%

---

# TVSDK 3.13 voor opmerkingen bij de release van iOS {#tvsdk-for-ios-release-notes}

TVSDK 3.12 voor iOS Release-notities beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK iOS 3.12.

## Systeem- en softwarevereisten {#system-software-requirements}

Voordat u iOS 3.12 downloadt, moet u controleren of uw hardware-, besturingssysteem- en toepassingsversies aan de volgende vereisten voldoen:

Besturingssysteem: iOS 8.0 of hoger.

## iOS TVSDK 3.13

De release introduceert ondersteuning voor DEMUXED &#39;HLS/CMAF&#39; (preroll, midroll en postroll)-advertenties voor LIVE-, VOD- en FER-streams.

Voor oplossingen voor door de klant gemelde problemen raadpleegt u [Opgeloste problemen](#resolved-issues). Zie voor beperkingen [bekende problemen en beperkingen](#known-issues-and-limitations).

### Nieuwe functies en oplossingen in de vorige versies {#whats-new-previous}

**iOS TVSDK 3.12**

Probleem verholpen waarbij de live stream na 15 minuten afspelen mislukt.

**iOS TVSDK 3.11**

Opgeloste problemen voor klanten `isFallbackOnInvalidCreativeEnabled` en methode `customParams` toepassing vastlopen.

**iOS TVSDK 3.10**

* Probleem verholpen waarbij de TVSDK-speler niet werd geactiveerd `PTMediaPlayerStatusError` bericht als het netwerk niet beschikbaar is.

**iOS TVSDK 3.9**

* Probleem verholpen waarbij VTT-ondertitels niet worden afgespeeld en de app vastloopt.

* iOS TVSDK 3.9 bevat het bijgewerkte certificaat voor individualisatietransport.

**iOS TVSDK 3.8.0.83 Hotfix**

De hotfix had het bijgewerkte certificaat van het individualiseringsvervoer.

**iOS TVSDK 3.8**

iOS 13-compatibiliteit en verwerking iOS 13 `UIWebView` API-afleiding.

**iOS TVSDK 3.7**

Hotfix voor een scenario waar het spelen tegengehouden wanneer vele verzoeken van de advertentieresolutie gelijktijdig werden gemaakt.

**iOS TVSDK 3.6**

**Oplossingen in de eigenschap wideXML van de klasse`PTNetworkAdInfo`**

De `vastXML` eigenschap werd niet correct ingesteld en retourneert een nulwaarde.

**iOS TVSDK 3.5**

**Achtergrondaudio inschakelen**

*Configureer uw app om door te gaan met het afspelen van audio wanneer deze naar de achtergrond gaat.*

Om deze functie in te schakelen, moeten we de nieuwe API instellen `audioPlaybackInBackground` toegevoegd in de `PTMediaPlayer` klasse. Als deze API is ingeschakeld, is uw app gereed om achtergrondaudio af te spelen.

**iOS TVSDK 3.4.0.19 (hotfix)**

Deze versie heeft een moeilijke situatie voor de toepassingsneerstortingen die in een ad failover scenario voorkomen.

**iOS TVSDK 3.4**

**Time-out voor resolutie van advertentie**

* Met TVSDK 3.4 kunnen gebruikers nu de time-outwaarde instellen voor algemene ad-resolutie en duidelijke downloads. Als sommige advertenties niet binnen een bepaalde tijd zijn opgelost, speelt TVSDK de resterende advertenties af.

* `PTAdMetadata: adRequestTimeout` API is vervangen en wordt verwijderd. De standaardwaarde is ingesteld op 35 seconden.

* Er zijn twee nieuwe alternatieve API&#39;s geïntroduceerd in de `PTAdMetadataClass: adResolutionTimeout`  - time-out voor algemene aanroepen voor adManifestTimeout - time-out voor ad-manifest-downloads.

**Opbrengstoptimalisatie**

TVSDK is ingeschakeld om probleemgebieden met betrekking tot werkstromen voor het toevoegen van toevoegingen te identificeren en aan het eindpunt van een analyse te rapporteren.

**Versie 3.3**

TVSDK 3.3 is nu compatibel met iOS 11 SDK. Alle vervangen API&#39;s zijn vervangen door geschikte alternatieven.

**Versie 3.2**

**Extra ondersteuning voor logboekregistratie (fase 2)**

Extra ondersteuning voor foutmeldingen in het geval van:

* De HLS-versie van de advertentie gebruikt een hoger niveau dan de inhoud.

* Alleen-audio variant is uitgesloten.

* VAST/VMAP request is failed.

**Versie 3.1**

* **Extra ondersteuning voor logboekregistratie**
Toegevoegde ondersteuning voor beschrijvende meldingen als er afspeelproblemen met de advertentie optreden.

* **Toegevoegd [!DNL Fairplay] Ondersteuning voor gecodeerde CMAF-stroom**
   [!DNL Fairplay] Gecodeerde CMAF-streams met afspelen van AVC-codec worden nu ondersteund.

**Versie 3.0.1**

Geen nieuwe functie of verbeteringen in deze release.

**Versie 3.0**

* TVSDK 3.0 ondersteunt HEVC-streams.

* Even in tijd - Adverterend advertenties dichter aan advertenties.

Toegevoegd `enableDelayAdLoading` eigenschap van het type Boolean in de interface op toepassingsniveau om JIT in te schakelen. Indien `enableDelayAdLoading` is NO, zal `setadMetadata.delayAdLoading`naar True (eigenschap van PTAdMetadata-interface).

Als deze eigenschap is ingeschakeld, worden alle ad-hocafbrekingen vóór de positie opgelost op basis van de gedefinieerde tolerantiewaarde. Standaard, `delayAdTolerance` wordt ingesteld op vijf seconden.

**Versie 1.4.45**

Om aan Xcode10 te voldoen, is TVSDK bewogen van `libstdc++` tot `libc++`en daardoor is de minimaal ondersteunde versie iOS 7. Eerder was het iOS 6.

**Versie 1.4.44**

Geen nieuwe functie of verbeteringen in deze release.

**Versie 1.4.43**

* TV-achtige ervaring met het midden van een advertentie kunnen deelnemen zonder dat gedeeltelijke advertentie wordt bijgehouden.\
   Voorbeeld: De gebruiker verbindt zich in het midden (bij 40 seconden) van een 90 seconde en onderbreking die uit drie 30 seconden bestaat. Dit is 10 seconden in de tweede advertentie in de pauze.

   * De tweede advertentie wordt afgespeeld gedurende de resterende duur (20 sec.), gevolgd door de derde advertentie.
   * Er worden geen trackers voor de gedeeltelijke advertentie geactiveerd (tweede advertentie). De trackers voor alleen de derde advertentie worden geactiveerd.

* Toegevoegd `enableVodPreroll` eigenschap van het type Boolean in de PTAdMetadata-interface. De eigenschap kan worden gebruikt om pre-roll in een VoD-stream in te schakelen. Indien `enableVodPreroll` NEE, PSDK speelt niet pre-roll. Dit heeft echter geen invloed op de halverwege de rol. De standaardwaarde van `enableVodPreroll` is JA.
* `closedCaptionDisplayEnabled` API van `PTMediaPlayer` De interface is vanaf iOS v1.4.43 gemarkeerd als afgekeurd. Bepalen of gesloten bijschriften beschikbaar zijn voor een bepaalde `PTMediaPlayerItem`de `subtitlesOptions` eigenschap van `PTMediaPlayerMediaItem`.

**Versie 1.4.42**

Er worden geen nieuwe functies toegevoegd aan deze release. Voor een lijst met opgeloste problemen raadpleegt u [Opgeloste problemen](#resolved-issues).

**Versie 1.4.41**

API-wijzigingen:

* **isSecure**: Een nieuwe API wordt geïntroduceerd isSecure om de speler te beveiligen tegen het opnemen en genereren van een fout. De standaardwaarde is true.

* **allowExternalRecording**: Er is een nieuwe API geïntroduceerd waarmee airplay-mirroring voor beveiligde inhoud wordt toegestaan. Airplay mirroring wordt daarom als opname beschouwd `allowExternalRecording` waarde moet worden ingesteld op `True`, om airplay mirroring toe te staan of in te stellen op `False` om de airplay-mirroring voor beveiligde inhoud te stoppen. Standaard, `value` is waar.

**Versie 1.4.40**

Geen nieuwe functies.

**Versie 1.4.39**

* iOS TVSDK is gecertificeerd met VHL 2.0.1 en met VHL 2.0.1 met Nielsen.

* iOS TVSDK wordt bijgewerkt om CRS-aanvragen van de nieuwe Akamai-host in te dienen `primetime-a.akamaihd.net`.

* De nieuwe hostnaamconfiguratie verstrekt activa CRS levering via zowel HTTP als HTTPS (SSL) op grotere schaal.

**Versie 1.4.36**

Integreer en certificeer VHL 2.0 in iOS TVSDK: Verminder de barrière in de `VideoHeartbeatsLibrary` door de complexiteit van de API&#39;s te verminderen.

**Versie 1.4.34**

**Netwerk en informatie**

TVSDK API&#39;s bieden nu aanvullende informatie over VAST-reacties van derden. Advertentienummer, Advertentiesysteem en VAST-advertentieverlengingen zijn beschikbaar in `PTNetworkAdInfo` klasse toegankelijk via  `networkAdInfo`  eigenschap op een advertentie-element. Deze informatie kan worden gebruikt voor integratie met andere analytische hulpmiddelen, zoals **Mat Analytics**.

**Versie 1.4.31**

* **Factureringscijfers** Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek verzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.

   Telkens wanneer TVSDK een gebeurtenis van het stroombegin produceert, begint de speler de berichten van HTTP periodiek aan Adobe systeem te verzenden. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de werkelijke waarden.

* **Ondersteuning voor meerdere CDN&#39;s voor CRS-advertenties** TVSDK ondersteunt nu Multi-CDN voor CRS-advertenties. Door FTP-gegevens op te geven voor CRS-advertenties, kunt u andere CDN-locaties opgeven dan de standaard Adobe-CDN, zoals [!DNL Akamai].

**Versie 1.4.29**

In de `PTSDKConfig` de klasse `forceHTTPS` API is toegevoegd.

De `PTSDKConfig` Deze klasse biedt methoden om SSL af te dwingen voor aanvragen die zijn ingediend bij Adobe Primetime en voor beslissings-, DRM- en Video Analytics-servers. Zie voor meer informatie de `forceHTTPS` en `isForcingHTTPS` methoden voor deze klasse. Als een manifest over HTTPS wordt geladen, behoudt TVSDK het inhoudsgebruik van HTTPS en eerbiedigt dit gebruik wanneer het laden van om het even welke relatieve URLs van dat manifest.

>[!NOTE]
>
>Verzoeken naar domeinen van derden, zoals het bijhouden van pixels voor toevoegen, inhoud en URL&#39;s voor toevoegen en vergelijkbare verzoeken, worden niet gewijzigd. Het is de verantwoordelijkheid van inhoudsproviders en servers om URL&#39;s op te geven die via HTTPS worden ondersteund.

**Versie 1.4.18**

Primetime iOS TVSDK biedt nu ondersteuning voor JavaScript 2.0-creatieve VPAID 2.0-services voor een rijke interactieve in-stream ad-ervaring. Voor meer informatie over VPAID 2.0, zie VPAID en steun.

**Versie 1.4.17**

* tvOS

   De TVSDK ondersteunt native tvOS-toepassingen.
* De volgende typen inhoud kunnen worden afgespeeld:

   * VOD
   * Live
   * AES-128
   * Alternatieve audio en ondertitels
   * FER

* De volgende typen advertenties kunnen worden weergegeven:

   * Basis
   * VAST2
   * VAST3
   * VMA

* De volgende functies worden momenteel niet ondersteund:

   * Digital Rights Management (DRM)
   * Advertentiebanners
   * Tv Markup Language (TVML)

**Versie 1.4.13**

>[!NOTE]
>
>De Nielsen-module is verwijderd uit de TVSDK-build en de TVSDK wordt binnenkort bijgewerkt met een nieuwe Nielsen-integratiemodule.

**Ad Fallback, Daisy chaining in ad selection logic (Zendesk #3103)**

Voor VAST-advertenties (creatieven) waarvoor de terugvalregel is ingeschakeld, behandelt de TVSDK een advertentie met een ongeldig MIME-type als een lege advertentie en probeert deze om terugvaladvertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren. Zie Extra fallback voor VAST- en VMAP-advertenties voor meer informatie.

**Versie 1.4.9**

**Blackout-signalering met vervanging van alternatieve inhoud**

In het kader van de 1.4-TVSDK-update ondersteunt Adobe nu ook het in- en terugkeren van regionale stroomuitval tegen lineaire inhoud. De TVSDK kan nu twee manifestbestanden parallel, hoofdbestand en alternatief verwerken om te controleren op uitstroomsignalen, zelfs wanneer alternatieve programmering wordt weergegeven in plaats van de oorspronkelijke programmering.

**Versie 1.4.8**

**Video Heartbeats Library (VHL) bijgewerkt naar versie 1.5**

* Mogelijkheid om metagegevens te verzenden met het starten van de video of het starten van de video/advertentie/hoofdstuk als contextgegevens.

* Minder netwerkverkeer - De hartslagen zijn gemiddeld minder en kleiner in grootte.

**Versie 1.4.7**

* **Ondersteuning voor individuele support op locatie**

Steun voor op-gebouw installaties van de Server van de Individualisering van de Adobe om het de individualisatieverzoek van de cliënt aan te passen om naar een verschillend eindpunt te gaan.

* **Op resolutie gebaseerde uitvoerbeveiliging**

In DRM-beleid kan nu de hoogst toegestane resolutie worden opgegeven, afhankelijk van de uitvoerbeveiligingsmogelijkheden van het apparaat. Bijvoorbeeld: _Als HDCP beschikbaar is, laat u het afspelen van inhoud tot een resolutie van 1080p toe en als HDCP niet beschikbaar is, laat u het afspelen van inhoud tot een resolutie van 480p toe._

**Versie 1.4.4**

* **Video Heartbeats Library (VHL)-update naar versie 1.4.1.1**

   * De mogelijkheid om verschillende analytische gebruiksscenario&#39;s te bundelen, van andere SDK&#39;s of spelers, met de Adobe Analytics Video Essentials.
   * Het bijhouden van advertenties is geoptimaliseerd door het verwijderen van de `trackAdBreakStart` en `trackAdBreakComplete` methoden. Het ad-einde wordt afgeleid van het `trackAdStart` en `trackAdComplete` methodeaanroepen.
   * De `playhead` Deze eigenschap is niet meer nodig voor het bijhouden van advertenties.
   * Toegevoegde ondersteuning voor de Experience Cloud ID-service.

* **Integratie van Nielsen SDK**

TVSDK ondersteunt nu het verzenden van mTVR- en MDPR ID3-beacons naar de Nielsen SDK zonder aangepaste integratie. Download de 3.1.2.19 Nielsen iOS App SDK en volg de instructies in de iOS Programmers Guide om aan de slag te gaan.

**Versie 1.4.0**

* **Blackout-signalering met vervanging van alternatieve inhoud**

In het kader van de 1.4-TVSDK-update ondersteunt de TVSDK nu ook het in- en terugkeren van regionale stroomuitval tegen lineaire inhoud. De TVSDK kan nu twee manifestbestanden parallel, hoofdbestand en alternatief verwerken om te controleren op uitstroomsignalen, zelfs wanneer alternatieve programmering wordt weergegeven in plaats van de oorspronkelijke programmering.

* **C3-advertenties verwijderen/vervangen**

Er is nu geen extra voorbereidend werk nodig om nieuwe advertenties dynamisch in video-op-verzoek (VOD)-elementen in te voegen die uit het C3-venster komen. De TVSDK beschikt nu over een API waarmee u aangepaste inhoudsbereiken kunt verwijderen en dynamisch nieuwe advertenties kunt invoegen. Deze krachtige nieuwe functionaliteit is ook handig in gevallen waarin live/lineaire inhoud tijdens de uitzending wordt gerepareerd en onmiddellijk wordt afgetrokken voor gebruik als inhoud op aanvraag zonder dat er voldoende tijd is om het middel schoon te maken.

## Opgeloste problemen {#resolved-issues}

Wanneer de resolutie aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond, bijvoorbeeld ZD#xxxxx.

<!-- 

Comment Type: draft

 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 

-->

<!--
Comment Type: draft

 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 
-->

**iOS TVSDK 3.13**

* (ZD 42085) - Problemen met afspelen op CMAF-streams.

* (ZD-43215) - De speler wordt vastgelopen wanneer de speler wordt verwijderd terwijl een advertentie wordt uitgevoerd.

* (ZD 43210) - Het afspelen van iOS HLS loopt vast wanneer WebVTT-ondertitel is ingeschakeld.

**iOS TVSDK 3.12**

* Live stream mislukt na 15 minuten afspelen bij gebruik van TVSDK voor iOS 3.10.

### Opgeloste problemen in de vorige releases {#resolved-issues-previous}

**iOS TVSDK 3.11**

* (ZD#40998) - De `isFallbackOnInvalidCreativeEnabled` zorgt dat de toepassing vastloopt.

* (ZD#41289) - `NSInvalidArgumentException` wordt waargenomen met de methode `customParams` waardoor de toepassing vastloopt.

**iOS TVSDK 3.10**

(ZD#40943) - De TVSDK-speler wordt niet geactiveerd `PTMediaPlayerStatusError` bericht als het netwerk niet beschikbaar is.

**iOS TVSDK 3.9**

(ZD#40272) - iOS TVSDK kan geen VTT-ondertitels afspelen met een fout van 101001 en de app wordt vastgezet.

**iOS TVSDK 3.8**

* (ZD#40087) - iOS crasht met spelerfout voor verlopen VOD-inhoud.

* (ZD#40083) - Pre-Roll-advertenties spelen niet met livestream `OpportunityGenerator` en de speler geeft een fout.

* (ZD#39828) - `CurrentItem` de annotatie voor nullability ontbreekt, waardoor de speler vastloopt wanneer de status van de speler in het bericht `PTMediaPlayerStatusStopped`.

**iOS TVSDK 3.7**

(ZD#38961) - Inhoud kan niet worden afgespeeld in het PiP-venster (Picture-in-Picture) nadat één inhoud is afgespeeld, wanneer meerdere inhoud is geconfigureerd om te worden afgespeeld in de PiP.

**iOS TVSDK 3.6**

Geen nieuwe problemen in deze release.

**iOS TVSDK 3.5**

Geen nieuwe problemen in deze release.

**Versie 3.3**

(ZD#37820) - Toegevoegd staat plaatsing op de lijst voor aangepaste koptekst HS-ID, HS-SSAI-TAG toe.

**Versie 3.2**

* **Ticket#36588** - Player crasht wanneer de STOP-methode van MediaPlayer wordt aangeroepen.

Correctie van het periodiek vastlopen dat werd waargenomen wanneer de STOP-methode wordt aangeroepen voor een paar streams met ondertitels.

* **Ticket#37080** - Dubbele verzoeken die voor Duidelijke vraag worden gezien.
Oplossing voor de dubbele aanvragen voor Manifest-URL&#39;s tijdens het afspelen. TVSDK doet nu één vraag per manifest.

* **Ticket#37** - De CRS-normalisatieregel mislukt met eq-match-type Fixed een case waarbij de speler vastliep bij de laatste normalisatieregel die voor hostnamen met een &quot;eq&quot;-match-type was ingesteld.

**Versie 3.1**

**Ticket #36313** - Intermitterende onvoorspelbare resultaten tijdens lineaire advertentie-einden Vaste afspeelintermitterende tijdens lineaire en onderbrekingen in Live stream.

**Versie 3.0.1**

**Ticket36948** - CRS - De volgorde voor de selectie van activa is inconsistent op iOS 12 Het voor CRS geselecteerde middel is niet altijd de variant van de hoogste kwaliteit die in een VAST- of VMAP-respons wordt geretourneerd.

**Versie 3.0**

* **Ticket35311** - De status van de speler wordt niet GEPAUZEERD tijdens een onderbreking van de telefoonvraag Toegevoegde onderbreekt manager om de speler tegen te houden die onderbreekt. Na onderbreking wordt de spelerstatus gepauzeerd en wordt het afspelen hervat wanneer u op de afspeelknop klikt.

* **Ticket36685** - Live assets - Tijd die niet overeenkomt met de voortgang van de spelertijd en tijd van de SCTE-markeerteken De juiste tijd wordt berekend voor de SCTE-markeertekens die vóór het actieve punt liggen.

* **Ticket36492** - `currentTime` en `localTime` niet worden bijgewerkt wanneer het zoeken naar een nieuwe positie tijdens de pauzestatus de huidige tijd van de Speler van de pauzestatus kan nu aan nul worden geplaatst voor het geval de speler in gepauzeerde staat is; eerder dan de huidige tijd die alleen in afspeelstatus op nul werd ingesteld.

**Versie 1.4.45**

* **Ticket36294** - iOS TVSDK werkt niet met Xcode 10. Oplossingen voor compilatieproblemen met TVSDK op XCode 10. Vanwege de vereisten voor XCode 10, vereisen apps die op TVSDK voor iOS 1.4.45 en hoger bouwen een minimaal implementatiedoel als iOS 7.0

* **Ticket36321** - Discrepantie waargenomen in een zoekbaar bereik tussen `PTMediaPlayer` en `AVPlayer` instantie in _Afspelen_ status.

* **Ticket36493** - `libstdc++` iOS 12 biedt ondersteuning voor het oplossen van compilatieproblemen met TVSDK op iOS 12. Voor toepassingen die zijn gebaseerd op TVSDK voor iOS 1.4.45 en hoger is minimaal implementatiedoel vereist als iOS 7.0

**Versie 1.4.44**

* **Ticket34683** - Afspeeltijd van advertentie is negatief

Extra controles die worden uitgevoerd om het geval te behandelen wanneer er een wanverhouding tussen de duur die door de advertentieserver wordt gemeld en daadwerkelijke advertentie-inhoud is.

* **Ticket34801** - `currentTime` en `localTime` werden niet bijgewerkt toen het zoeken naar een nieuwe positie tijdens de pauzestatus de huidige tijd van de Speler van de pauzestatus nu aan nul kan worden geplaatst voor het geval de speler in gepauzeerde staat is; eerder dan de huidige tijd die alleen in afspeelstatus op nul werd ingesteld.

* **Ticket35037** - Afspelen van afspeelstallen met een slechte URL bij het terugkeren van signaalgebaseerde invoeging.
Verbeterde oplossing voor afgesloten uitgave #34385 in release 1.4.42. Toegevoegde isCanceled controle en uitzondering behandelende code om verrichtingsrij robuuster te maken.

**Versie 1.4.43**

* (ZD#32990) - iOS: Inhoud afspelen in plaats van advertenties op bepaalde actiepunten. `selectedMediaOptionInMediaSelectionGroup` API die deel uitmaakte van de AVPlayerItem-interface is nu onder `AVMediaSelection` in iOS 11. Het probleem is opgelost met deze nieuwe API.

* (ZD#33683) TVSDK verwijderd `==` aan de meta-gegevenskoorden achtervoegsel. Het probleem is opgelost in de parseringslogica.

* (ZD#33905) - iOS TVSDK die vraag aan de manifestdossiers met twee gebruikersagenten maakt. Het probleem met de gebruikersagent is opgelost in de eerste m3u8-aanroep (nieuwbouw). M3u8&#39;s hebben nu dezelfde gebruiker-agenten voor alle aanroepen.

* (ZD#34293) - Op LINEAR-streams ingevoegde voorrollen worden niet correct afgespeeld in iOS11. Het probleem is opgelost voor pre-roll advertenties.

* (ZD#34684) - Wanneer het beleid voor het overslaan van advertenties wordt toegepast, worden pre-roll en frames gedurende een paar seconden weergegeven. een nieuwe API, `enableVodPreroll` is geïntroduceerd om het afspelen vóór de rol in het afspelen van het wachtwoord uit te schakelen. De standaardwaarde voor deze API is _Ja_. De API zorgt ervoor dat de inhoud van de hoofdinhoud wordt overgeslagen.

* (ZD#34765) - Na het aanroepen `stop()`Er worden nog maar weinig transportstreamsegmenten gedownload. Verbeterde het `Stop()` API om te voorkomen dat de extra segmenten worden gedownload.

* (ZD#34865) - Pre-roll advertenties voor [!DNL Livestream] worden afgekapt op iOS. Dit probleem is opgelost. Dit probleem is te maken met iOS11 en er wordt een extra controle aan toegevoegd om te bevestigen of de stream pre-roll of main-content is.

* (ZD#35093) - Oplossing voor een failover-scenario waarbij, als de Primaire variant van de stream bij het opstarten mislukt (404 wordt geretourneerd), het afspelen niet naar de back-upstream wordt geschakeld.

**1.4.42 (1.4.42.118)**

* (ZD#34385) - Afspeelstallen met een ongeldige URL bij het terugkeren van op signaal gebaseerde invoeging.

   Maximumaantal gelijktijdige controles verhogen voor `CustomAVAssetLoaderOperations`, zodat de leesbewerkingen van het manifest kunnen worden voortgezet.

* (ZD#34373) - Eindgebruikers kunnen niet streamen naar met HDMI aangesloten apparaten wanneer het opnemen van streams wordt verboden.

* (ZD#32678) - TVSDK verzamelt de juiste id&#39;s voor de advertentie niet op iOS.

   Advertentie-id van de uiteindelijke advertentie-creatief wordt nu opgenomen in VHL-pingelt als er sprake is van omleiding van VAST/VMAP.

* (ZD#33904) - TVSDK is niet geregistreerd voor AVFFoundation-kennisgevingen `AVAudioSessionMediaServicesWereLostNotification` en `AVAudioSessionMediaServicesWereResetNotification`.

   `PTMediaServicesWereLostNotification` en `PTMediaServicesWereResetNotification` kan nu worden geregistreerd in de speler-app om de meldingen op te halen wanneer de mediaservices opnieuw worden ingesteld of verloren gaan.

* (ZD#33815) - Klanten kunnen hun regels voor prioritering en normalisatie van CRS niet bijwerken zonder een app-update te vereisen.

   De `getCRSRulesJsonURL` en `setCRSRulesJsonURL` API&#39;s voor de iOS TVSDK.

**Versie 1.4.41 (1.4.41.76)**

* (ZD #34464) - Issues building Reference App met TVSDK Version 1.4.41

   Als u deze versie start, is Xcode 9 vereist voor het compileren van TVSDK voor iOS.
* (ZD #29456) - Airplay start in de pauzestatus

   Het probleem met de pauze dat optreedt wanneer de video wordt gepauzeerd bij het invoeren van Airplay is opgelost.
* (ZD #30371) - De begintijd van AdBreak verandert wanneer wij meer dan twee advertenties in lineaire stroom opnemen

   Correctie van de fout bij het afspelen van inhoud op Apple TV, waardoor het afspelen niet volledig kan worden uitgevoerd.
* (ZD #32146)- Nee `PTMediaPlayerStatusError` is ontvangen voor HLS Live-inhoud op het blokkeren van iOS 11 dev bèta

   Nee `PTMediaPlayerStatusError` wordt ontvangen voor HLS Live- en VOD-inhoud bij het blokkeren met Charles (verbinding Drop en 403).

* (ZD #29242) - Het afspelen van Airplay-video mislukt met advertenties ingeschakeld.

   Wanneer advertenties zijn ingeschakeld en AirPlay is ingeschakeld, wordt het afspelen van een video gestart, het afspelen van de video wordt nooit gestart en er wordt geen fout weergegeven.

* (ZD#33341) - `DRMInterface.h` triggers genereren waarschuwingen in Xcode 9.

   Oplossing voor twee blokprototypen in `DRMInterface.h` die in hun parameterlijsten het woord &#39;void&#39; ontbraken.

* (ZD#31979) - Wordt niet gecompileerd/uitgevoerd als het iOS 10 of hoger is voor iPhone 7/iPhone7+.

   Vaste IB-documenten die ouder zijn dan iOS 7 worden niet meer ondersteund.

* (ZD#32920) - Leeg scherm binnen een Advertentiesonderbreking en geen Ad-onderbreking voltooiing.

   Wanneer een Ad-einde Ad-instanties weergeeft en nadat een advertentie-instantie is voltooid, wordt een leeg scherm weergegeven.

* (ZD#32509) - iOS 11-schermopname uitschakelen Schermopname uitschakelen in iOS 11.

* (ZD#33179) - Gebeurtenisfout met tussenpozen in iOS11.

   Oplossing voor de gebeurtenisfout in iOS 11.

**Versie 1.4.40** (1.4.40.72)

* (ZD #32465) - Speler kan samengevoegde playlists niet behandelen.

   Bellen `finishLoadingWithError`(met: Fout) voor AV stichting om afwisselende stromen/trekker failover te proberen.

* (ZD #31951) - TVSDK-fout tijdens rotaties van licentie.

   Probleem met rotatie van licentie opgelost.
* (ZD #31951) - Leeg scherm binnen een Ad-einde en geen Ad-break-voltooiing.

   Probleem opgelost waarbij Facebook VPAID-advertenties vaak meerdere CDATA-blokken in één enkele kamer retourneren `<AdParameters>` VAST-knooppunt.
* (ZD #33336) - iOS TVSDK - Advertentiepods worden niet gevuld, ondanks dat er voldoende advertenties zijn geretourneerd door Freewieltje.

   Gemaakt bovenliggend-onderliggend verband tussen reeks en fallback en sorteren op basis van bovenliggende reeks en index.

**Versie 1.4.39** (1.4.39.43)

* (ZD #32178) - De iOS TVSDK-versie is onjuist.

   De uitvoer van de TVSDK-versie in de logbestanden was 1.0.211. Het is vast om de juiste versie uit te voeren.

* (ZD #32199) - Lazy Ad loading - Video wordt niet weergegeven voor de inhoud.

   De lokale tijdlijn van Adbreak die niet eerder werd geïnitialiseerd, wordt nu vernieuwd voor gebruik.

* (ZD #27528) - Video, audio of beide bevriezen 1-45 seconden nadat het afspelen van een element is gestart, als de secundaire audio op iOS 1.2 is ingesteld op niet-standaard.

   Audiotracks voorbereiden en informeren in de gebruiksstatus.

* (ZD #30411) - Als u een secundaire taal voor Opslaan kiest, krijgt u mogelijk onverwachte resultaten, zoals geen audio of onjuiste audio.

   Audiotracks voorbereiden en informeren in de gebruiksstatus.

* (ZD #32199) - Lazy Ad loading - Video wordt niet weergegeven voor de inhoud.

   De lokale tijdlijn van Adbreak die niet eerder werd geïnitialiseerd, wordt nu vernieuwd voor gebruik.

* (ZD #27528) - Video, audio of beide bevriezen 1-45 seconden nadat het afspelen van een element is gestart, als de secundaire audio op iOS 1.2 is ingesteld op niet-standaard.

   Audiotracks voorbereiden en informeren in de gebruiksstatus.

* (ZD #30411) - Als u een secundaire taal voor Opslaan kiest, krijgt u mogelijk onverwachte resultaten, zoals geen audio of onjuiste audio.

   Audiotracks voorbereiden en informeren in de gebruiksstatus.

**Versie 1.4.38** (1.4.38.860)

* (ZD #29281) - iOS: AdSystem en Creative ID toevoegen aan CRS-aanvragen

Gebruik van creatieve ID en AdSystem in CRS- verzoek dat op de normalisatieregels van CRS wordt gebaseerd

* (ZD #29176) - Crash on `PTAdPolicyDeligate` `satAdBreakAsWatched:position`

Crash due to empty AdBreak wordt nu afgehandeld.

* (ZD #30125) - Programmatische advertenties werken niet op iOS-platform

Extra ondersteuning voor programmatische advertenties in iOS.

* (ZD #30782) - #EXT-X-PROGRAMM-DATE-TIME Melding

Gebeurtenis met getimede metagegevens wordt niet geactiveerd voor # EXT-X-PROGRAMM-DATE-TIME-tags met LIVE DRM-streams.

**Versie 1.4.37 (1.4.37.842)**

* (ZD #28950 ) - Probleem met afspelen van VOD

Probleem met afspelen wanneer de tag # EXT-X-PLAYLIST-TYPE in de stream is ingesteld op Gebeurtenis in plaats van VOD

* (ZD #29281) - iOS: AdSystem en Creative ID toevoegen aan CRS-aanvragen

Gebruik van Creative ID en AdSystem in CRS-verzoek op basis van de regels voor CRS-normalisatie.

* (ZD #29462) - TremorHub en A&amp;E VOD die een crash veroorzaken in iOS apps

**Versie 1.4.36 (1.4.36.835)**

* (ZD #29418) - Gebruik met tijdsduur 0 (#EXT-X-CUE-OUT:0.000) zorgt ervoor dat iOS TVSDK het afspelen stopt of vastloopt.

Het probleem is opgelost en het afspelen wordt op de juiste wijze gestart.

* (ZD #29462) - Advertentie bij VOD die ertoe leidde dat de iOS TVSDK vastliep.

Het probleem is opgelost. iOS TVSDK brengt een `exception(AUDNetworkAdInfo::initWithAdId)` en niet omgaan. De uitzondering wordt veroorzaakt door een lege advertentie-ID.

* (ZD #29281) - Voeg AdSystem en Creative id toe aan CRS-aanvragen.

Neem AdSystem en CreativeId op als nieuwe parameters in de verzoeken 1401 en 1403 (alle andere parameters blijven hetzelfde).

**Versie 1.4.35** (1.4.35.830)

* (ZD #27830) - Moet het verschil tussen closed-captions en subtitle in iOS programmatisch bepalen.

TVSDK stelt nu de twee typen beschikbaar die kunnen worden gebruikt om het vereiste bijschrifttype uit te filteren.

* (ZD #29160) - EXT-X-CUE-OUT en aanwijzingen worden niet correct weergegeven op TVSDK iOS.

Met de EXT-X-CUE-OUT-midroll-advertentie wordt nu afgespeeld.

* (ZD #29100) - De app loopt vast wanneer de gebruiker naar het einde van een film scrubt.

Oplossing voor meerdere crashes met betrekking tot synchronisatie.

* (ZD #28785), (ZD #27712) en (ZD #25076) - De iOS-app crasht tijdens de grote livegebeurtenissen.

Oplossing voor meerdere crashes met betrekking tot synchronisatie.

**Versie 1.4.34** (1.4.34.815 voor iOS 6.0+)

* (ZD #28481) - FER-outage vanwege een onjuiste toets die wordt toegevoegd aan het einde van een advertentieeinde voor die FER-streams

Voor een FER-stream wordt de toets voor het ad-einde ingevoegd na het einde van het ad-einde. Dit probleem is opgelost door het toevoegen van de *laatst weergegeven sleutel* aan het einde van het advertentieeinde.

**Versie 1.4.33** (1.4.33.803 voor iOS 6.0+)

* (ZD# 21701) CRS inschakelen voor subrekeningen

Ingeschakeld door de oorspronkelijke creatieve URL voor de 1401 CRS-aanvraag te verzenden in plaats van de genormaliseerde URL, volgens de vereiste voor CRS-back-end.

* (ZD# 26218) - `PSDKResources.bundle` ladingkwestie

Dit probleem is opgelost door het laden van bronnen bij te werken en uit alle beschikbare bundels te zoeken.

* (ZD# 27460) Midroll eerste Ad vraag - POST aan `cdn.auditude.com` terugzending 403.

Het nieuwe CDN-account kan een CDN-aanvraag van een POST niet verwerken. Dit probleem is opgelost door de code bij te werken om de `cdn.auditude.com` en verzoek om GET in plaats van POST te zijn.

**Versie 1.4.32** (1.4.32.792 voor iOS 6.0+)

* (ZD# 27132) Ondersteuning voor decimale waarden voor VMAP Ad Breaks.

Wanneer de inhoud niet langs de gedefinieerde ad-hocafbrekingen werd gesegmenteerd, veroorzaakten gehele getallen onverwachte ad-positionering. Het probleem is opgelost door de decimale waarden niet om te zetten in gehele getallen.

* (ZD# 27189) AES-inhoud met de EXT-X-DISCONTINUITY-SEQUENCE-tag wordt niet correct afgespeeld.

Het probleem is opgelost door de tag aan het begin van de afspeellijst te plaatsen.

**Versie 1.4.31** (1.4.31.785 voor iOS 6.0+)

* (ZD# 24528) Gebruikswaarden voor TVSDK implementeren voor facturering

Zie voor meer informatie [Factureringscijfers].

* (ZD# 24642) Picture-in-Picture support for TVSDK

De beeld-in-beeld functie, die soms niet goed werkte, is opgelost.

* (ZD# 25246) Onjuiste e-mails

Dit probleem is opgelost door discontinuïteitscodes op verschillende manifests uit te lijnen.

* (ZD# 26218) Het proces voor het samenstellen van de toepassing wordt gecompliceerd bij het opnemen van de toepassing `PSDKLibrary.framework` in het toepassingsframework van de client

Dit probleem is opgelost door de `PSDKLibrary.framework` op verzoek.

* (ZD# 26364) Ondersteuning voor meerdere CDN&#39;s voor CRS-advertenties

Zie Meerdere CDN-ondersteuning voor CRS en levering voor meer informatie.

* (ZD# 27028) Vertraging bij het afspelen van sommige streams in iOS 10.

Dit probleem is opgelost door een oplossing te bieden voor streams die geen M3U8-extensie hebben.

**Versie 1.4.30** (1.4.30.754 voor iOS 6.0+)

De volgende problemen zijn in deze release opgelost voor TVSDK:

* (ZD# 24180) Voeg een aangepaste koptekst toe aan de lijst van gewenste personen.

Er is een nieuwe aangepaste koptekst toegevoegd aan de lijst van gewenste personen TVSDK.

* (ZD# 25016) Failover-stroom wordt willekeurig geselecteerd wanneer ABR-besturingsparameters worden ingesteld

Dit probleem is opgelost door de ABR-stromen op orde te houden op het moment dat de ABR-instellingen bij de `initialBitrate` het plaatsen op een stroom die failover URLs omvat. Dit vermijdt het spelen van de failoverstromen in plaats van primair.

* (ZD# 25076) Crash on `PTAuditudeAdResolver loadComplete`

Het probleem waarbij een crash optrad tijdens het snel starten/stoppen van meerdere PTMediaPlayer-instanties met advertenties is opgelost.

* (ZD# 25960) Geen extra ingetekende markeringen die het bericht van de meta-gegevensverandering teweegbrengen uitzendingen

De kwestie waar een geabonneerde markering niet wordt meegedeeld wanneer het verschijnt alvorens het eerste segment in manifest is bevestigd.

* (ZD# 26084) PSDK met 106000,101000.-11833-decoder heeft geen fout aangetroffen bij het overschakelen van de laatste en het afbreken naar entertainmentinhoud

Wanneer de laatste begintijd van de advertentie-break van de VMAP valt voordat de totale duur is voltooid, wordt in bepaalde omstandigheden de toets pas ingevoegd na het einde van het laatste ad-break. Dit probleem is opgelost.

* De videokaart (VHL) is bijgewerkt naar versie 1.5.9 om de volgende problemen op te lossen:

* (ZD #22351) VHL - Analytics: Duur van live video-element

Dit probleem is opgelost door het toevoegen van de  `assetDuration`  API naar `PTVideoAnalyticsTrackingMetadata` om de elementduur voor live/lineaire streams bij te werken en een logica te bieden voor het controleren van de live stream.

* (ZD# 22675) VHL - Analytics: De duur van live video-elementen bijwerken

Dit probleem is hetzelfde als ZD #22351.

* (ZD #25908) VHL - Analytics: Adobe hartslaggebeurtenis vastloopt

Dit probleem is opgelost door de implementatie bij te werken en de nieuwste versie van VHL voor iOS versie 1.5.9 te gebruiken om de stabiliteit en de prestaties te verbeteren.

* (ZD #25956) VHL - Analytics: Vastlopen bij het herhaaldelijk afspelen van video&#39;s

Dit probleem is hetzelfde als ZD #25908.

**Versie 1.4.29** (1.4.29.743)

* (ZD# 23901) Advertenties van derden worden niet afgespeeld

Dit probleem is opgelost door naar de URL-structuur van CRS v3 te gaan en de zone-id op te nemen in de opnieuw verpakte URL.

* (ZD #25183) Problemen met het afspelen van DRM op tvOS en iOS

Dit probleem is opgelost door ondersteuning te bieden voor meerdere toetstags die nodig zijn voor ondersteuning voor multi-DRM.

* (ZD# 25334) TVSDK kan geen gedeelde cDVR-inhoud afspelen

Dit probleem is opgelost door te voorkomen dat TVSDK lege tekenreeksen omzet in absolute URL&#39;s.

* (ZD# 25347) Aangepaste HTTP-header instellen op AVURLAsset

Ondersteuning voor aangepaste koppen op zijn segmentaanvragen via de `PTNetworkConfiguration` -klasse is toegevoegd.

**Versie 1.4.28** (1.4.28.722)

* (ZD #24549) Veelvoudige en volgende vraag

Dit probleem is opgelost door het tijdlijnbeheer bij te werken en te luisteren naar meldingen over een specifiek object wanneer meerdere spelers zijn gemaakt.

* (ZD #24758) `PTManifestLogger` biedt geen ondersteuning voor iOS 8

Dit probleem is opgelost door de logger-hulpprogrammabibliotheek bij te werken naar het implementatiedoel voor versie 7.0.

* (ZD #24775) Vertraagde stream vanwege advertenties

Dit probleem is opgelost door de tijdsverloop op afspeellijsten van gebeurtenissen correct te berekenen.

* (ZD #24799) Sommige afleveringen worden niet afgespeeld op de APP van iOS

Dit probleem is opgelost door de lokale webserver te gebruiken voor ondertitels wanneer de WebVTT-bestanden beperkt zijn.

**Versie 1.4.27** (1.4.27.711) voor iOS 6.0+

* (ZD #24089) - Optimalisaties voor en oplossingen voor lange DVR-streams

Dit probleem is opgelost door meerdere optimalisaties toe te voegen om de tijd te verminderen die nodig is om het DVR-venster in live/lineaire streams te verwerken.

* (ZD #21554) - Foutbeacons voor TVSDK niet geactiveerd voor `application-type = video/mp4`

Dit probleem is opgelost door de speler in staat te stellen de juiste URL&#39;s voor het bijhouden van fouten op ongeldige elementindelingen te pingelen.

* (ZD #24424) - Crash of type `EXC_BAD_ACCESS KERN_INVALID_ADDRESS` afkomstig is van binnenuit `PSDKLib` voor iOS op nieuwere hardwareapparaten.

De crash die optrad als gevolg van een niet-toegewezen mediaspelerinstantie, waarbij het afspelen snel tussen verschillende streams wordt geschakeld, is opgelost.

* (ZD #24575) - Crash in TVSDK op 32-bits apparaten wanneer `enableDebugLog=true`

De kwestie in het logboekformaat dat de botsing op apparaten met 32 bits veroorzaakte wanneer het registreren wordt toegelaten is opgelost.

**Versie 1.4.26** (1.4.26.702) voor iOS 6.0+

* (ZD# 20213) - TVSDK FW moet dynamisch/gemoduleerd zijn voor XCode7

De bibliotheken zijn bijgewerkt met ondersteuning voor modules.

**Versie 1.4.25** (1.4.25.684) voor iOS 6.0+

* (ZD #19629) - Live video wordt gepauzeerd bij het betreden van Airplay naar ATV 4

Dit probleem is opgelost door een wachttijd toe te voegen nadat je oude objecten hebt verwijderd, maar voordat je nieuwe objecten toevoegt aan de `AVQueuePlayer`. Zonder de wachttijd worden meldingen verzonden naar het onjuiste object.

* (ZD #19856) - Geen ondertitels worden weergegeven wanneer deze standaard zijn ingeschakeld

De problemen in de webvtt-afspeellijst, waardoor de ondertitels niet correct werden weergegeven, zijn opgelost.

* (ZD #21590) - Videoprestaties en tracering in de nieuwste Origin Builds

Het probleem met de ontbrekende videolengte in `VideoAnalytics` is opgelost.

* (ZD #20202) - De iOS-app loopt vast door aangepaste opmaakstijlen voor ondertitels in te stellen

Dit probleem is opgelost door extra null-objectcontroles toe te voegen tijdens het instellen van ondertitelingsstijlen.

* (ZD #20709) - videolengte gerapporteerd als 0 in video start tracking

Dit probleem is hetzelfde als (ZD #21590).

* (ZD #22280) - De videolengte van Analytics wordt ingesteld op 0

Dit probleem is hetzelfde als (ZD #21590).

* (ZD #22592) - Problemen met Airplay in Primetime

Dit probleem is hetzelfde als (ZD #19629).

* (ZD#22922) - Handmatige bitsnelheidsomschakeling voor iOS

Dit probleem is opgelost met een optie voor het opgeven van de maximale bitsnelheid.

* (ZD #23084) - Apple-compatibiliteit voor IPv6-netwerken

De symbolen die niet door Apple werden aanbevolen voor IPv6-compatibiliteit zijn verwijderd.

**Versie 1.4.24** (1.4.24.661) voor iOS 6.0+

* ZD #2548) - Primetime ondersteuning voor interactieve reclame op mobiele apparaten - VPAID 2.0

Dit probleem is opgelost door de logica bij te werken om de weergave van de speler ongedaan te maken als een VPAID-advertentie niet wordt afgespeeld.

* (ZD #20101) - Bij de implementatie van Aangepast hoofdstuk wordt de gebeurtenis start van het hoofdstuk tijdens het afspelen van het document geactiveerd

Dit probleem is opgelost door het bijwerken `VideoAnalyticsTracker` om hoofdstukbegin/voltooiing behoorlijk te ontdekken wanneer het overgaan tussen hoofdstuk en niet-hoofdstukgrenzen.

* (ZD #20784) - Analyse: Het triggeren van inhoud wordt voltooid voor live video-overgangen

Dit probleem is opgelost door een logica toe te voegen die handmatig het voltooien van de inhoud tijdens een sessie voor het bijhouden van video activeert.

De volgende bibliotheken zijn bijgewerkt:

* AdobeMobile-bibliotheek naar 4.10.0
* VHL-bibliotheek naar 1.5.6
* VHL-Nielsen-bibliotheek naar 1.6.7
* (ZD #21855) - Ondertitels worden niet afgespeeld na de middelste rol

In dit geval leidden dubbele discontinuïteitslabels ertoe dat ondertitels niet na de middelste rol werden weergegeven. Dit probleem is opgelost door de volgende discontinuïteitscodes te verwijderen.

* (ZD #21994) - Tekenreeks buiten de grenzen `PTHLSUtils`

De meest waarschijnlijke oorzaak van de botsing is wanneer een EXT-x-SLEUTEL een URL heeft die door citaten wordt omringd.

* ZD #22074) - `AUDVAST` Eenmaal per minuut crashen in iOS

In versie 1.4.23 is de crash hersteld die werd veroorzaakt door de aanwezigheid van onveilige tekens in een VAST-URL voor omleiding. TVSDK bleef deze advertenties echter overslaan.

Dit probleem is opgelost door de onveilige tekens te verwerken en de advertenties af te spelen.

* (ZD #22694) - `PTMediaPlayer`.  Weergave is verborgen voor speler

Dit probleem is opgelost door de logica bij te werken om de weergave van de speler ongedaan te maken als een VPAID-advertentie niet wordt afgespeeld.

**Versie 1.4.23** (1.4.23.641) voor iOS 6.0+

* (ZD #18016) - Geen reactie van Primetime SDK met een slechte netwerkvoorwaarde

Dit probleem is opgelost door foutmelding te verbeteren als er een fatale fout is opgetreden `AVFoundation` treedt op en zorgt ervoor dat de toepassing het opnieuw starten na de fout kan afhandelen.

* (ZD #20580) - Crash in `PTSplicerManager`

Dit probleem is opgelost door extra bescherming te bieden tegen gelijktijdige problemen die de crash veroorzaken.

* (ZD #21782) - iOS-foutcode 10100

Het probleem waarbij de TVSDK een fout van 101000 heeft geretourneerd bij het starten van het afspelen op DRM-streams van Adobe Access is opgelost.

* (ZD #21889) - Onlineadvertenties en het afspelen van offline inhoud mislukt

Het probleem waarbij het afspelen mislukte nadat een advertentie met met AES gecodeerde offline inhoud was opgelost.

* (ZD #22074) - AUDVAST crasht eenmaal per minuut op iOS

Dit probleem is opgelost door de verwerking van VAST-tags van derden met ongeldige tekens in de URL te verbeteren.

* (ZD #22257) - De TVSDK kan de DRM-stream niet afspelen

Het probleem waarbij de TVSDK die een fout van 101000 heeft geretourneerd terwijl het afspelen werd gestart op DRM-streams van Adobe Access, is opgelost.

**Versie 1.4.22** (1.4.22.627) voor iOS 6.0+

* (ZD #18709) - Crash in de TVSDK voor iOS

Het probleem met een crash die optrad bij bepaalde met DRM beveiligde streams van Adobe Access is opgelost.

* (ZD #18850) - Creatieve selectielogica bijwerken op basis van CRS-regels

Dit probleem is opgelost door een .json-configuratiebestand toe te voegen waarin de prioriteit voor creatieve selectie wordt opgegeven.

* (ZD #19770) - Beveiligde AES-videofeed wordt niet meer afgespeeld

Het probleem waarbij bepaalde 302 omgeleide stromen niet speelden, is opgelost.

* (ZD #19629) - Live video wordt gepauzeerd bij het betreden van Airplay naar ATV 4

Dit probleem is opgelost door een tijdelijke oplossing toe te voegen voor het onderbreken van live video wanneer airplay is ingeschakeld voor Apple TV 4-apparaten. Het probleem lijkt een Apple TV 4-probleem te zijn.

* (ZD #21119) - De TVSDK wordt na het afspelen van de advertentie gestopt

Er is ondersteuning toegevoegd voor met AES gecodeerde streams met een reeks IV tijdens het gebruik van een invoegtoepassing.

* (ZD #21125) - Terugkeer van begin van leven/lineair en break

Er is ondersteuning toegevoegd voor het retourneren van een advertentie-einde vroeg voordat het advertentieeinde wordt afgespeeld. De vroege terugkeer wordt vermeld door een markering van douanemanifest.

* (ZD #21224) - Airplay-ondersteuning voor verdeelde streams van Akamai

API&#39;s zijn toegevoegd aan de `PTNetworkConfiguration` klasse om cookies toe te voegen als URL-parameters op segmenten voor bepaalde Akamai-gebonden streams.

* (ZD #21287) - Onzuiverheden

Een kwestie met sommige logboekverklaringen die door gebrek in de xcode console worden getoond zelfs wanneer het registreren gehandicapt is bevestigd.

* (ZD #21446) - Gebeurtenissen van Ad Break die soms niet door de TVSDK worden geactiveerd

Bij EVENT-streams worden geen correcte regeleinden geactiveerd in de vorige releasebuild. Deze build verhelpt dit probleem.

**Versie 1.4.21** (1.4.21.605) voor iOS 6.0+

* (ZD #20749) - Bij fallback worden niet-lege VAST-reacties overgeslagen; URL&#39;s met extra URL&#39;s en tekstspatiëring worden geactiveerd

Er is een probleem opgelost met dubbele pingen op terugvaladvertenties.

**Versie 1.4.20** (1.4.20.590) voor iOS 6.0+

* (ZD #18639) - De TVSDK gebruikt buitensporige CPU/bronnen op een langdurig opnameapparaat

Het buitensporige CPU/middelengebruik is op twee niveaus vastgelegd. Eerst door de functie van de tijdupdate op een globale rij, in plaats van de belangrijkste draad te laten lopen, en door het gebruik van cpu voor het ontleden van manifest met eerder verwerkte en caching m3u8 te optimaliseren.

* (ZD #19349) - Pre-Roll advertenties worden overgeslagen wanneer het vertragen van de netwerkverbinding.

Dit probleem is opgelost door een time-outgebeurtenis (requestTimeout) op te geven aan de toepassing en de `adMetadata.adRequestTimeout` API om de standaardtime-out van 10 seconden te overschrijven.

* (ZD #19446) - Melding ontbreekt voor Live streams

Dit probleem is opgelost door de toepassing toe te staan zich te abonneren op de `EXT-X-PROGRAM-DATE-TIME` op live streams.

* (ZD #19459) - Crash bij het voorbereiden van alternatieve audio met `PTMediaPlayerItem` `prepareAudioOptionsWithAVMediaSelectionOptions`
* (ZD #19460) - Crash - `[PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]`

Dit is hetzelfde als Zendesk #19459.

* (ZD #19574) - De TVSDK retourneert geen M3U8-responsgegevens voor DRM- of niet-DRM-inhoud

In de eerste keer dat het manifestbestand in `PTMediaPlayerItem.prepareToPlay`Indien het laden van het manifest is mislukt, rapporteert de TVSDK de hoofdtekst van de mislukkingsreactie op de toepassing niet.

Dit probleem is opgelost door de TVSDK toe te staan de mislukkingsreactie als een fout aan de toepassing te melden.

* (ZD #19615) - Back-uplogica werkt niet

In de huidige implementatie zijn fallback-advertenties overgeslagen en niet opnieuw verpakt, tenzij deze advertenties de indeling m3u8 hebben. Dit probleem is opgelost door ook ondersteuning toe te voegen voor het opnieuw verpakken van fallback-advertenties.

* (ZD #19770) - De TVSDK kan geen beveiligde AES-inhoud afspelen met 302 omleiding

Het probleem met de omleiding is opgelost, omdat de omleidings-URL werd weggevaagd door `cleanConnectionData` voordat het manifest kon worden geparseerd.

* (ZD #19856) - Ondertitels worden niet voor sommige bitsnelheden weergegeven als dit standaard is ingeschakeld

Dit probleem is opgelost door de fout van iOS af te handelen voor de segmenten van de streams waarin de ondertitels niet worden weergegeven.

* (ZD #19868) - De TVSDK loopt vast als een ongeldige creatieve persoon wordt verhandeld

Het neerstorten in de TVSDK waarbij een instantie van de grote parser ten onrechte werd toegewezen, is opgelost.

* (ZD #20180) - VPAID-advertenties worden af en toe overgeslagen

JavaScript-mime-type werd niet altijd opgenomen of beschouwd als een geldig mime-type. Dit probleem is opgelost door JavaScript op te nemen als een geldig MIME-type.

* (ZD #20749) - Bij fallback worden niet-lege VAST-reacties overgeslagen; URL&#39;s met extra URL&#39;s en tekstspatiëring worden geactiveerd

De kwestie waar sommige van de creatieve producten niet opnieuw worden verpakt, is opgelost.

**Versie 1.4.19** (1.4.19.563) voor iOS 6.0+

* ZD #18639) - De TVSDK gebruikt buitensporige CPU/bronnen op een langdurig opnameapparaat

Dit probleem is opgelost door de DRM m3u8-afspeellijst te optimaliseren en te herschrijven naar cachebits van de afspeellijst die eerder zijn herschreven. Dit is het meest relevant wanneer u live m3u8-streams afspeelt waarvoor de m3u8 wordt gedownload na elke segmentdownload.

* (ZD#18956) - `player.drmManager` is nul wanneer het onderbrekingspunt in iOS Demo Player wordt ingesteld

Dit probleem is opgelost door het `PTMediaPlayer.drmManager` API-implementatie om DRMManager op te halen van het DRM-framework.

**Versie 1.4.18** (1.4.18.557) voor iOS 6.0+

* (ZD #18844) Afspeelkop bijhouden voor live-inhoud in de iOS-speler.

Dit probleem is opgelost door de toepassingen toe te staan hun eigen waarde voor de afspeelkop in te stellen.

* (Zendesk #18518) - Als de naam van de video niet is opgegeven, wordt de naam van TVSDK standaard ingesteld op * PSDK-speler.*

Dit probleem is opgelost door de standaardwaarde voor de naam van de speler te verwijderen.

**Versie 1.4.17** (1.4.17.545) voor iOS 6.0+

* (Zendesk #2228) - Verbeter TVSDK om JSON-reactie van het ophalen van een manifest terug te sturen

In plaats van een fout te verzenden wanneer de inhoud niet M3U8 is, retourneert het DRM-framework een nul-DRMM-metagegevens. Het probleem is opgelost door metagegevens toe te voegen om inhoud beschikbaar te maken wanneer de melding M3U8_PARSER_ERROR plaatsvindt.

* (Zendesk #2231) - Fout die van het halen van manifest niet beschikbaar in MediaPlayerNotification is teruggekeerd

Dezelfde resolutie als Zendesk #2228

* (Zendesk #3304) - VAST 3.0 `[ERRORCODE]` macro niet gevuld

De kwestie waar [!DNL Auditude] SDK kan niet verzenden pingelt wanneer volgende URL ruimten aan het begin heeft opgelost.

* (Zendesk #17294) - Crash [!DNL SecKeyRawSign]

Een mogelijke crash wanneer de code van de klant de sleutelketen gebruikt is opgelost.

* (Zendesk #18008) - Ondersteuningscookies voor iOS8+ voor ondersteuning van gebonden streams

Voor speciaal voor Akamai geoptimaliseerde streams is het vereist dat cookies worden verzonden op segmentaanvragen. Dit was niet mogelijk in iOS 7 en eerder. Vanaf iOS 8 heeft Apple een API toegevoegd waarmee cookies kunnen worden doorgegeven voor segmentaanvragen. Deze ondersteuning is nu beschikbaar in de TVSDK. Er is ook ondersteuning toegevoegd voor het verzenden van een gebruikersagent, indien beschikbaar.

* (Zendesk #18166) - TVSDK 1.4.15 geeft honderden waarschuwingen bij compilatie met `DWARF` with `dSYM` bestandsopties

Alle waarschuwingen zijn opgelost.

**Opmerking**: Er zijn tvOS-compatibele bibliotheken toegevoegd voor TVSDK.

**Versie 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Tab S loopt vast tijdens het afspelen

De afhankelijkheid van OKHTTP herstellen [!DNL Auditude] voor CRS omdat TVSDK nu rechtstreeks gebruikmaakt van de `httpurlconnection` in plaats van krullen. Het probleem werd opgelost door uitzonderingen te verhelpen voordat een nieuwe JNI-oproep werd gedaan.

* (Zendesk #4487) - Lineair kanaal van inhoud volgen

Het probleem is opgelost door de videohartslagtracker tijdens een lineaire streamafspeelsessie opnieuw te initialiseren.

* (Zendesk #17919) - Android - bij het zoeken naar inhoud treedt een hartslagfout op

Het probleem was om de hartslag in een foutenstaat op te lossen wanneer er een vraag in een hoofdstuk is

* (Zendesk #18053) - Toepassing met de TVSDK-crash bij Marshmallow

De TVSDK liep vast op Android™ M OS toen de TVSDK-bibliotheek neoncode gebruikt die YUV doet `->` RGB-kleuromzetting. Dit probleem is opgelost door de functies die dit probleem veroorzaken bij te werken met een niet-neonversie van `code`.

* (Zendesk #18072) - Android M - Toepassing vastloopt

Deze crash gebeurt tijdens het aanroepen `MediaCodecList` en `MediaCodecInfo` API&#39;s wanneer wordt gecontroleerd of het profiel en het niveau worden ondersteund. Adobe zoekt naar Google-ondersteuning voor meer inzicht. Dit probleem is opgelost door een tijdelijke oplossing te bieden door alle codec-informatie van tevoren te laden, zodat deze API&#39;s niet alleen hoeven te worden aangeroepen wanneer codec-informatie nodig is.

* (Zendesk #18074) - Arabische ondertitels die niet werken op Nexus met Android™ 6.0

Dit probleem is opgelost door ondersteuning voor de Android™ CTS-lettertypetoewijzing.

**Versie 1.4.15** (1.4.15.512) voor iOS 6.0+

**Opmerking**: De Nielsen-module is verwijderd uit de TVSDK-build, maar de TVSDK wordt binnenkort bijgewerkt met een nieuwe Nielsen-integratiemodule.

* (ZD #2228) - Fout die van het halen van manifest niet beschikbaar in is teruggekeerd `MediaPlayerNotification`

Metagegevens toegevoegd om inhoud tijdens het bericht beschikbaar te maken `M3U8_PARSER_ERROR` voorkomt.

* (ZD #4437) - Crashes inside Adobe Primetime SDK

Probleem verholpen waarbij het programma vastloopt tijdens het voorbereiden van ondertitels/alternatieve audio.

* (ZD #4487) - Lineair kanaal van inhoud volgen

Herinitialisatie van de videohartslagtracering is toegestaan tijdens een lineaire streamafspeelsessie.

**Versie 1.4.14** (1.4.14.498) voor iOS 6.0+

* (ZD #17260) - Crash on `playlistManagerForURL`

Probleem verholpen waarbij een periodiek crash optrad als gevolg van gelijktijdige uitvoering.

**Versie 1.4.13** (iOS 6.0+)

* (ZD #3304) - VAST 3.0 `[ERRORCODE]` macro niet gevuld

   * Foutcode 400 wordt weergegeven als de inline een slechte creatieve functie heeft.
   * `[ERRORCODE]` macro is URL-gecodeerd.

* (ZD #3865) Integratie van hartslag met IMA-advertenties

Het probleem waarbij de videolengte onjuist werd gerapporteerd, is opgelost.

* Bijgewerkte TVSDK-demospeler ter ondersteuning van iOS 9

Om iOS 9 behoorlijk te steunen, moet u de uitzonderingen van de Veiligheid van het Vervoer van de Toepassing vormen. Voor de demo is de ATS volledig uitgeschakeld.

**Versie 1.4.12** (1.4.12.464) voor iOS 6.0+

* (ZD #4521) CRS Testing Client Side and SSAI

Correctie van onjuiste reverse MD5 in 3P URL.

**Versie 1.4.12** (1.4.12.463) voor iOS 6.0+

* (ZD #2751) CSAI en CRS / Verbeteren: Dynamische elementen in bepaalde URL&#39;s van mediabestanden verwerken.

Bijgewerkte Creative Repackaging Service voor het correct verwerken van advertenties met dynamische creatieve URL&#39;s.

* (ZD #3654) Geheugenlek in PSDK-versie na 1.3.4.166

Vaste geheugenlek in `drmFramework` met standaardweergave op iOS 8.2-apparaten

* (ZD #3988) Preroll wordt overgeslagen wanneer het zoeken terug in het na eerste playback

Oplossing van een bug zodat advertentiebeleid correct kon worden uitgeschakeld.

* (ZD #4017) iOS API aanvragen om bestanden op achterwaartse wijze te forceren en af te spelen

Opgelost met fix voor ZD #4279

* (ZD #4279) HLS TVSDK en invoeging -302 redirect issue on iOS and Desktop

Het probleem waarbij een advertentie-element gebruikmaakte van een relatieve omleiding naar de URL, is opgelost.

**Versie 1.4.9** (1.4.9.427) voor iOS 6.0+

* (ZD #3075) Internet Reachability Issue - iOS

Er is een melding toegevoegd om te detecteren wanneer het afspelen is gestopt.

* (ZD #3193) Verzoek om een API voor profielwijziging in TVSDK

Bijgewerkt `PTPlaybackInformation` om de bijgewerkte aangegeven bitsnelheid weer te geven. Bijgewerkt `BITRATE_CHANGE` een melding dat de bitsnelheden van de M3U8 betrouwbaarder en nauwkeuriger zijn.

* (ZD #3324) Primetime advertenties die een probleem melden als er geen advertentiemedia in VMAP zijn

Door TVSDK worden lege URL&#39;s voor het bijhouden van regeleinden ondersteund en worden de begin- en eindwaarden voor lege advertentieafbrekingen gecontroleerd.

**Versie 1.4.8** (1.4.8.402)

* (ZD #3158) IOS 7 crasht bij volledige gebeurtenisreplay

**Versie 1.4.7** (1.4.7.382)

* (ZD #2197) Fouten opvolgen en opsporen. Toegevoegde melding voor element kan manifest niet laden.
* (ZD #2894) Speler maakt vier top-level duidelijke verzoeken tijdens playback.
* (ZD #2992) [!DNL Auditude] Meldende vreemde tijdsduur en herkenningstekens.

**Versie 1.4.6**(1.4.6.325)

* (ZD #2197) Fouten opvolgen en opsporen. Toegevoegde melding voor element kan manifest niet laden

**Versie 1.4.5** (1.4.5.283)

* (ZD #2141) Implementatie van analysemogelijkheden voor [!DNL TreeHouse] app, toegevoegd `AdobeAnalyticsPlugin.a` bibliotheek om pakket samen te stellen.
* Video Heartbeats Library update naar 1.4.1.2
* (PTPALY-4226) (gerelateerd aan ZD #2423) Het uitvoeren van DRM-resetten kan resulteren in het verwijderen van gegevens in het toepassingsdocument.

**Versie 1.4.4** (1.4.4.242)

* Video Heartbeats Library (VHL)-update naar 1.4.1.

* (ZD #2435) TV SDK-documentatie over analysemogelijkheden moet worden bijgewerkt

**Versie 1.4.2** (1.4.2.2010 : iOS 6.0+)

* (ZD #1129) `_player.currentItem.audioOptions` leeg retourneren
* (ZD #2109) Primetime PSDK 1.4.1.125 werkt niet met Xcode 5.1.1
* (ZD #2137) Crash in PSDK op iOS wanneer DRM-metagegevens niet kunnen worden geladen

**Versie 1.4.1**(1.4.1.125)

* (ZD #1107) [!DNL CocoaLumberjack] dubbele symbolen
* (ZD #1644) iOS User Agent for Targeting and Reporting wijzigen
* (ZD #1850) Cacao Lumberjack files included in iOS SDK
* (ZD#1908) Aangepaste tags worden genegeerd door PSDK als er meer dan 1 is

**Versie 1.4.0** (1.4.0.32)

* Zendesk #1024 - Functie voor het verwijderen van advertenties uit de stream via manifest

## Apparaatcertificering en ondersteuning {#device-certification-and-support}

>[!NOTE]
>
>De volgende functies zijn **niet** ondersteund in de TVSDK:
>
>* Trage beweging op elk platform of elke versie.
>* Live truc.


**Versie 1.4.43**

* TVSDK 1.4.43 is gecertificeerd voor iOS 11.

**Versie 1.4.29**

* TVSDK 1.4.29 is gecertificeerd voor iOS 10.

**Versie 1.4.28**

* TVSDK 1.4.28 is gecertificeerd voor iOS 10 Beta 7.
* DRM-ondersteuning om HTTPS te forceren door toevoegen  `forceHTTPS`  en `isForcingHTTPS` API&#39;s.
* Bijgewerkte bibliotheken VHL aan 1.5.8, Adobe Mobiele bibliotheken aan 4.8.4, en de logger nutsbibliotheek aan versie 7.0 plaatsingsdoel.

**Versie 1.4.19**

Deze versie van de TVSDK is gecertificeerd met de FairPlay-ondersteuning voor iOS en tvOS.

**Versie 1.4.17**

* tvOS

   Deze versie van de TVSDK biedt ondersteuning voor tvOS en is gecertificeerd voor niet-gecodeerde HLS-streams.

   **Opmerking**: Houd rekening met de volgende compilatierichtlijnen:

   * TVSDK tvOs-ondersteuning is beperkt tot niet-Adobe DRM gecodeerde streams. U moet de verwijzing verwijderen naar `drmNativeInterface.framework` in uw tvOS-ontwikkelinstellingen. Met AES gecodeerde stromen worden nog steeds ondersteund.
   * Apple vereist dat alle Apple TV-toepassingen zijn ingeschakeld voor bitcode. U moet deze markering dus in de projectinstellingen inschakelen.

## Bekende problemen en beperkingen {#known-issues-and-limitations}

* Ten gevolge van de afgekeurde iOS UIWebView-klasse, vanaf iOS TVSDK 3.6:
   * VPAID-advertenties worden niet afgespeeld zoals wordt verwacht in iPad 13.
   * Companion-advertenties spelen niet zoals verwacht.

* In iOS TVSDK worden alle advertenties vastgezet in het contentmanifest. Advertentiepatronen worden geïmplementeerd door te zoeken op basis van de duur van de inhoud en advertentiesegmenten. Dus als de duur van het segment niet nauwkeurig is, eindigt het zoeken mogelijk niet altijd bij het exacte frame van het begin of einde van het ad-einde. Zelfs als de duur van het frame beperkt is, is er een tolerantie die het platform zelf oplegt aan zoeken. Er kunnen enkele frames of advertenties of inhoud worden weergegeven. Dit is een beperking van het platform en de manier waarop en de invoeging werkt met TVSDK op iOS.
* Het besluit om over te slaan gebeurt in dit geval op de gebeurtenis seek. Aangezien de tijdsduur van het advertentiesegment in het manifest echter de werkelijke duur van de advertentie niet nauwkeurig vertegenwoordigt, is de zoekactie niet nauwkeurig. U ziet dus een paar frames advertentie wanneer het advertentiebeleid wordt toegepast.
* Het kan voorkomen dat Licentie-rotatievideo niet wordt afgespeeld op iOS 11 en dat deze goed wordt afgespeeld op iOS 9.x en iOS 10.x.
* Als bij VPAID 2.0-ondersteuning het afspelen via AirPlay actief is, worden VPAID-advertenties overgeslagen.
* De `drmNativeInterface.framework` wordt niet correct gekoppeld wanneer het minimumdoel is ingesteld op iOS7 (of hoger).
Oplossing: Geef expliciet de `libstdc++.6.dylib` bibliotheek als volgt: Ga naar **[!UICONTROL Target]** > **[!UICONTROL Build Phases]** > **[!UICONTROL Link Binary With Libraries]** en toevoegen `libstdc++.6.dylib`.
* Post-Roll Advertentie wordt niet ingevoegd voor vervangings-API.
* Als u een advertentie-einde zoekt (zonder er uit te komen), wordt een dubbel advertentie-begin- en advertentierapport weergegeven
* Instelling `currentTimeUpdateInterval` heeft geen effect.
Opmerking: In bepaalde iOS-versies laadt het besturingssysteem de bronnen in de `PSDKLibrary.framework` automatisch. Het is belangrijk dat u de `PSDKResources.bundle` op de bundelbronnen van de toepassing: Ga naar **Fasen samenstellen** en kopieert bundelbronnen.
* De Reference App kan niet worden samengesteld met behulp van Xcode 8 of lagere versies. Vanaf iOS TVSDK versie 1.4.41 kunt u Xcode 9 gebruiken om te compileren.
* VPAID-advertenties houden zich niet aan de `delayAdLoadingTolerance` waarde.
* 24077- Voor bepaalde HLS-inhoud met ondertitels loopt de speler vast op _Stoppen_ of _Herstellen_ methode.
* Gedetailleerde foutmeldingen zijn niet beschikbaar als Just in Time Ad resolving is ingeschakeld.
* Foutmeldingen worden geregistreerd volgens de resolutietijd van de advertentie en niet volgens de volgorde van de advertentie.
* HEVC-ondersteuning heeft de volgende beperkingen in deze release
   * DRM wordt niet ondersteund
   * CC-ondersteuning (CEA 608/708) is niet beschikbaar omdat deze niet wordt ondersteund in CMAF.
   * 4K-ondersteuning is nog niet aanwezig.
   * ID3-tags worden niet ondersteund, omdat deze niet worden ondersteund in CMAF.
   * Niet-gedempte live HEVC-streams zijn niet geverifieerd.
   * Ondersteuning voor HEVC-advertenties is niet geverifieerd.
* Als JIT is ingeschakeld en de tolerantie is ingesteld op 10 seconden, wordt geen VAST gesprek gezien voor de eerste midroll en break als er VMAP > VAST-leesadvertenties zijn.
* Time-out bij resolutie toevoegen werkt alleen correct als de afspeellijst telkens wordt bijgewerkt tijdens het afspelen van een live stream, en de speler een vastgezette afspeellijst verwacht binnen 20 sec. Als er binnen het genoemde interval geen vastgezette afspeellijst wordt ontvangen, wordt een interne fout gegenereerd en wordt de speler gestopt.

## Nuttige bronnen {#helpful-resources}

* [TVSDK 3.4 voor iOS-programmeergids](/help/programming/tvsdk-3x-ios-prog/ios-3x-introduction/ios-3x-overview/ios-3x-overview.md)
* [TVSDK iOS 3.4 API-naslaggids](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v34/index.html)
* Zie de volledige Help-documentatie op [Adobe Primetime - Meer informatie en ondersteuning](https://experienceleague.adobe.com/docs/primetime.html) pagina.
