---
title: Opmerkingen bij de release TVSDK 3.12 voor iOS
description: De opmerkingen bij de release TVSDK 3.12 voor iOS beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK iOS 3.12.
translation-type: tm+mt
source-git-commit: 9c6a6f0b5ecff78796e37daf9d7bdb9fa686ee0c
workflow-type: tm+mt
source-wordcount: '7665'
ht-degree: 0%

---


# Opmerkingen bij de release TVSDK 3.12 voor iOS {#tvsdk-for-ios-release-notes}

De opmerkingen bij de release TVSDK 3.12 voor iOS beschrijven wat nieuw of gewijzigd is, de opgeloste en bekende problemen en de apparaatproblemen in TVSDK iOS 3.12.

## Systeem- en softwarevereisten {#system-software-requirements}

Voordat u iOS 3.12 downloadt, moet u controleren of uw hardware-, besturingssysteem- en toepassingsversies aan de volgende vereisten voldoen:

Besturingssysteem: iOS 8.0 of hoger.

## iOS TVSDK 3.12

Probleem verholpen waarbij de live stream na 15 minuten afspelen mislukt.

Voor moeilijke situaties in de huidige versie zie [klantenkwesties die worden opgelost](#resolved-issues) en voor beperkingen zie [bekende kwesties en beperkingen](#known-issues-and-limitations) sectie.

### Nieuwe functies en oplossingen in de vorige versies {#whats-new-previous}

**iOS TVSDK 3.11**

Opgeloste oplossingen voor problemen van klanten waarbij `isFallbackOnInvalidCreativeEnabled` en de methode `customParams` ertoe leiden dat de toepassing vastloopt.

**iOS TVSDK 3.10**

* Probleem verholpen waarbij de TVSDK-speler geen melding `PTMediaPlayerStatusError` verzendt wanneer het netwerk niet beschikbaar is.

**iOS TVSDK 3.9**

* Probleem verholpen waarbij VTT-ondertitels niet konden worden afgespeeld waardoor de app vastliep.

* iOS TVSDK 3.9 bevat het bijgewerkte certificaat voor individualisatietransport.

**iOS TVSDK 3.8.0.83 Hotfix**

De hotfix had het bijgewerkte certificaat van het individualiseringsvervoer.

**iOS TVSDK 3.8**

Compatibiliteit met iOS 13 en verwerking iOS 13 UIWebView API-afleiding.

**iOS TVSDK 3.7**

Hotfix voor een scenario waarbij het afspelen werd gestopt wanneer een groot aantal verzoeken om ad-resolutie gelijktijdig werden ingediend.

**iOS TVSDK 3.6**

**Oplossingen in de eigenschap wideXML van de klasse`PTNetworkAdInfo`**

De eigenschap wideXML werd niet correct ingesteld en retourneert een nulwaarde.

**iOS TVSDK 3.5**

**Achtergrondaudio inschakelen**

*Configureer uw app om door te gaan met het afspelen van audio wanneer deze naar de achtergrond gaat.*

Om deze functie in te schakelen, moeten we de nieuwe API instellen die in de klasse PTMediaPlayer wordt `audioPlaybackInBackground` toegevoegd. Als deze API is ingeschakeld, is uw app gereed om achtergrondaudio af te spelen.

**iOS TVSDK 3.4.0.19 (hotfix)**

Deze versie heeft een moeilijke situatie voor de toepassingsneerstortingen die in een ad failover scenario voorkomen.

**iOS TVSDK 3.4**

**Time-out voor resolutie van advertentie**

* Met TVSDK 3.4 kunnen gebruikers nu de time-outwaarde instellen voor algemene ad-resolutie en duidelijke downloads. Als sommige advertenties niet binnen een bepaalde tijd zijn opgelost, worden de resterende advertenties afgespeeld door TVSDK.

* PTAdMetadata: de API voor adRequestTimeout is afgekeurd en wordt verwijderd. De standaardwaarde is ingesteld op 35 seconden.

* Er zijn twee nieuwe alternatieve API&#39;s geïntroduceerd in de PTAdMetadataClass: adResolutionTimeout - time-out voor algemene aanroepen van adManifestTimeout - time-out voor adManifest-downloads.

**Opbrengstoptimalisatie**

TVSDK is ingeschakeld om probleemgebieden met betrekking tot werkstromen voor invoegtoepassingen te identificeren en aan een analytisch eindpunt van de keuze te rapporteren.

**Versie 3.3**

TVSDK 3.3 is nu compatibel met de iOS 11-SDK. Alle vervangen API&#39;s zijn vervangen door geschikte alternatieven.

**Versie 3.2**

**Extra ondersteuning voor logboekregistratie (fase 2)**

Extra ondersteuning voor foutmeldingen in het geval van:

* De HLS-versie van de advertentie gebruikt een hoger niveau dan de inhoud.

* Alleen-audio variant is uitgesloten.

* VAST/VMAP request is failed.

**Versie 3.1**

* **Extra ondersteuning voor** logboekregistratie Toegevoegde ondersteuning voor beschrijvende meldingen in geval van afspeelproblemen met de advertentie.

* **Toegevoegde Fairplay Encrypted CMAF-stream ondersteuning** voor Fairplay Encrypted CMAF-streams met AVC-codec afspelen wordt nu ondersteund.

**Versie 3.0.1**

Geen nieuwe functie of verbeteringen in deze release.

**Versie 3.0**

* TVSDK 3.0 ondersteunt HEVC-streams.

* Even in tijd - Adverterend advertenties dichter aan advertenties.

Toegevoegde `enableDelayAdLoading` eigenschap van het type Boolean op interface op toepassingsniveau om JIT in te schakelen. Als `enableDelayAdLoading` NO is, zal het `setadMetadata.delayAdLoading`aan Waar (bezit van interface PTAdMetadata).

Als deze eigenschap is ingeschakeld, worden alle ad-hocafbrekingen vóór de positie opgelost op basis van de gedefinieerde tolerantiewaarde. Standaard `delayAdTolerance` is dit ingesteld op 5 seconden.

**Versie 1.4.45**

Om te voldoen aan Xcode10, is TVSDK van &quot;`libstdc++`&quot;naar &quot;`libc++`&quot;bewogen, en dientengevolge is de minimaal gesteunde versie iOS 7. Eerder was het iOS 6.

**Versie 1.4.44**

Geen nieuwe functie of verbeteringen in deze release.

**Versie 1.4.43**

* TV-achtige ervaring met het midden van een advertentie kunnen deelnemen zonder dat gedeeltelijke advertentie wordt bijgehouden.\
   Voorbeeld: De gebruiker verbindt zich in het midden (bij 40 seconden) van een 90 seconde en onderbreking die uit drie 30 seconden bestaat. Dit is 10 seconden in de tweede advertentie in de pauze.

   * De tweede advertentie wordt afgespeeld gedurende de resterende duur (20 sec.), gevolgd door de derde advertentie.
   * Er worden geen trackers voor de gedeeltelijke advertentie geactiveerd (tweede advertentie). De trackers voor alleen de derde advertentie worden geactiveerd.

* Toegevoegde enableVodPreroll-eigenschap van het type Boolean in de PTAdMetadata-interface. De eigenschap kan worden gebruikt om pre-roll in een VoD-stream in te schakelen. Als enableVodPreroll NO is, speelt PSDK niet pre-rol. Dit heeft echter geen invloed op de middenrollen. De standaardwaarde van enableVodPreroll is JES.
* closedCaptionDisplayEnabled API van de PTMediaPlayer-interface is gemarkeerd als afgekeurd vanaf iOS v1.4.43. Om te bepalen of gesloten titels voor een bepaalde PTMediaPlayerItem beschikbaar zijn, onderzoek het ondertitelingsbezit van PTMediaPlayerMediaItem.

**Versie 1.4.42**

Er worden geen nieuwe functies toegevoegd aan deze release. Zie [Opgeloste problemen](#resolved-issues)voor een lijst met opgeloste problemen.

**Versie 1.4.41**

API-wijzigingen:

* **isSecure**: Een nieuwe API wordt geïntroduceerd isSecure om de speler te beveiligen tegen het opnemen en genereren van een fout. De standaardwaarde is true.

* **allowExternalRecording**: Er is een nieuwe API geïntroduceerd waarmee airplay-mirroring voor beveiligde inhoud wordt toegestaan. Airplay mirroring wordt beschouwd als opname en daarom moet de `allowExternalRecording` waarde worden ingesteld op `True`, zodat airplay mirroring mogelijk is of wordt ingesteld om de airplay mirroring `False` te stoppen voor beveiligde inhoud. Standaard `value` is dit true.

**Versie 1.4.40**

Geen nieuwe functies.

**Versie 1.4.39**

* iOS TVSDK is gecertificeerd met VHL 2.0.1 en met VHL 2.0.1 met Nielsen.

* De iOS TVSDK wordt bijgewerkt en maakt daarom CRS-aanvragen van de nieuwe Akamai-host `primetime-a.akamaihd.net`.

* De nieuwe hostnaamconfiguratie verstrekt activa CRS levering via zowel HTTP als HTTPS (SSL) op grotere schaal.

**Versie 1.4.36**

Integreer en certificeer VHL 2.0 in iOS TVSDK: Verminder de hindernis in de `VideoHeartbeatsLibrary` implementatie door de complexiteit van de API&#39;s te verminderen.

**Versie 1.4.34**

**Netwerk en informatie**

TVSDK API&#39;s bieden nu aanvullende informatie over VAST-reacties van derden. Advertentie-ID, Ad System en VAST Ad Extensions worden aangeboden in `PTNetworkAdInfo` klassen die toegankelijk zijn via `networkAdInfo` eigenschap op een advertentie-element. Deze informatie kan worden gebruikt voor integratie met andere Analytics-advertentieplatforms, zoals **Moat Analytics**.

**Versie 1.4.31**

* **Factureringscijfers** Adobe verzamelt gebruiksmaatstaven en gebruikt deze maatstaven om te bepalen hoeveel de klanten moeten factureren, zodat ze kunnen betalen voor wat ze alleen gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik.

   Telkens wanneer TVSDK een streamstartgebeurtenis genereert, stuurt de speler regelmatig HTTP-berichten naar het factureringssysteem van Adobe. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de werkelijke waarden.

* **Ondersteuning voor meerdere CDN&#39;s voor CRS Ads** TVSDK ondersteunt nu Multi-CDN voor CRS-advertenties. Door FTP-gegevens op te geven voor CRS-advertenties, kunt u andere CDN-locaties opgeven dan de standaard CDN die in eigendom is van Adobe, zoals Akamai.

**Versie 1.4.29**

In de `PTSDKConfig` klasse is de forceHTTPS API toegevoegd.

De `PTSDKConfig` klasse biedt methoden om SSL af te dwingen voor aanvragen die zijn ingediend bij Adobe Primetime en bij het nemen van beslissingen, DRM en Video Analytics-servers. Zie de methoden `forceHTTPS` `isForcingHTTPS` en methoden in deze klasse voor meer informatie. Als een manifest over HTTPS wordt geladen, behoudt TVSDK het inhoudsgebruik van HTTPS en eerbiedigt dit gebruik wanneer het laden van om het even welke relatieve URLs van dat manifest.

>[!NOTE] Verzoeken naar domeinen van derden, zoals het bijhouden van pixels voor toevoegen, inhoud en URL&#39;s voor toevoegen en vergelijkbare verzoeken, worden niet gewijzigd. Het is de verantwoordelijkheid van inhoudsproviders en servers om URL&#39;s op te geven die via HTTPS worden ondersteund.

**Versie 1.4.18**

Primetime iOS TVSDK ondersteunt nu VPAID 2.0 Javascript-creatieven om een rijke interactieve functie in-stream en ervaring mogelijk te maken. Voor meer informatie over VPAID 2.0, zie VPAID en steun.

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

>[!NOTE] De Nielsen-module is verwijderd uit de TVSDK-build en de TVSDK wordt in de nabije toekomst bijgewerkt met een nieuwe Nielsen-integratiemodule.

**Ad Fallback, Daisy chaining in ad selection logic (Zendesk #3103)**

Voor VAST-advertenties (creatieven) waarvoor de terugvalregel is ingeschakeld, behandelt de TVSDK een advertentie met een ongeldig MIME-type als een lege advertentie en probeert deze om terugvaladvertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren. Zie Extra fallback voor VAST- en VMAP-advertenties voor meer informatie.

**Versie 1.4.9**

**Blackout-signalering met vervanging van alternatieve inhoud**

In het kader van de 1.4-TVSDK-update steunen wij nu ook het in- en terugkeren van regionale stroomuitval tegen lineaire inhoud. De TVSDK kan nu twee manifestbestanden parallel, hoofdbestand en alternatief verwerken om te controleren op uitstroomsignalen, zelfs wanneer alternatieve programmering wordt weergegeven in plaats van de oorspronkelijke programmering.

**Versie 1.4.8**

**Video Heartbeats Library (VHL) bijgewerkt naar versie 1.5**

* Mogelijkheid om metagegevens te verzenden met het starten van de video en/of het starten van de video/advertentie/hoofdstuk als contextgegevens.

* Minder netwerkverkeer - De hartslagen zijn gemiddeld minder en kleiner in grootte.

**Versie 1.4.7**

* **Ondersteuning voor individuele support op locatie**

Ondersteuning voor on-premise installaties van de Adobe Individualization Server om het individuele verzoek van de client aan te passen en naar een ander eindpunt te gaan.

* **Op resolutie gebaseerde uitvoerbeveiliging**

In DRM-beleid kan nu de hoogst toegestane resolutie worden opgegeven, afhankelijk van de uitvoerbeveiligingsmogelijkheden van het apparaat. Bijvoorbeeld: &quot;Als HDCP beschikbaar is, kan inhoud met een resolutie tot 1080p worden afgespeeld en als HDCP niet beschikbaar is, kan inhoud met een resolutie tot 480p worden afgespeeld.&quot;

**Versie 1.4.4**

* **Video Heartbeats Library (VHL)-update naar versie 1.4.1.1**

   * De mogelijkheid om verschillende analysemogelijkheden te bundelen, van andere SDK&#39;s of spelers, met de Adobe Analytics Video Essentials.
   * Het bijhouden van advertenties is geoptimaliseerd door de `trackAdBreakStart` en de `trackAdBreakComplete` methoden te verwijderen. Het ad-einde wordt afgeleid van de aanroepen van de methode `trackAdStart` `trackAdComplete` en de methode.
   * De `playhead` eigenschap is niet meer nodig voor het bijhouden van advertenties.
   * Toegevoegde ondersteuning voor de Bezoeker-id van de marketingcloud.

* **Integratie van Nielsen SDK**

TVSDK ondersteunt nu het verzenden van mTVR- en MDPR ID3-beacons naar de Nielsen SDK zonder aangepaste integratie. Download de 3.1.2.19 Nielsen iOS App SDK en volg de instructies in de iOS-programmagids op om aan de slag te gaan.

**Versie 1.4.0**

* **Blackout-signalering met vervanging van alternatieve inhoud**

In het kader van de 1.4-TVSDK-update ondersteunt de TVSDK nu ook het in- en terugkeren van regionale stroomuitval tegen lineaire inhoud. De TVSDK kan nu twee manifestbestanden parallel, hoofdbestand en alternatief verwerken om te controleren op uitstroomsignalen, zelfs wanneer alternatieve programmering wordt weergegeven in plaats van de oorspronkelijke programmering.

* **C3-advertenties verwijderen/vervangen**

Er is nu geen extra voorbereidend werk nodig om nieuwe advertenties dynamisch in video-op-verzoek (VOD)-elementen in te voegen die uit het C3-venster komen. De TVSDK beschikt nu over een API waarmee u aangepaste inhoudsbereiken kunt verwijderen en dynamisch nieuwe advertenties kunt invoegen. Deze krachtige nieuwe functionaliteit is ook handig in gevallen waarin live/lineaire inhoud tijdens de uitzending wordt gerepareerd en onmiddellijk wordt afgetrokken voor gebruik als inhoud op aanvraag zonder dat er voldoende tijd is om het element &#39;schoon&#39; te maken.

## Opgeloste problemen {#resolved-issues}

Wanneer de resolutie aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond, bijvoorbeeld ZD#xxxxx.

<!-- 

Comment Type: draft

<note type="note"> 
 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 
</note>

 -->

<!--
Comment Type: draft

<note type="note"> 
 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 
</note>
 -->
**iOS TVSDK 3.12**

* Live stream mislukt na 15 minuten afspelen bij gebruik van TVSDK voor iOS 3.10.

### Opgeloste problemen in de vorige releases {#resolved-issues-previous}

**iOS TVSDK 3.11**

* (ZD#40998) - De toepassing `isFallbackOnInvalidCreativeEnabled` loopt vast.

* (ZD#41289) - `NSInvalidArgumentException` wordt waargenomen bij de methode die tot het vastlopen van de toepassing `customParams` leidt.

**iOS TVSDK 3.10**

(ZD#40943) - De TVSDK-speler geeft geen PTMediaPlayerStatusError-melding wanneer het netwerk niet beschikbaar is.

**iOS TVSDK 3.9**

(ZD#40272) - iOS TVSDK kan geen VTT-ondertitels afspelen met een fout van 101001 en de app wordt vastgezet.

**iOS TVSDK 3.8**

* (ZD#40087) - iOS loopt vast met een spelerfout voor verlopen VOD-inhoud.

* (ZD#40083) - Pre-Roll-advertenties worden niet afgespeeld voor livestream met `OpportunityGenerator` en de speler geeft een fout.

* (ZD#39828) - `CurrentItem` eigenschap mist de annotatie voor nullability, waardoor de speler vastloopt wanneer de status van de speler in het bericht is `PTMediaPlayerStatusStopped`.

**iOS TVSDK 3.7**

(ZD#38961) - Inhoud kan niet worden afgespeeld in het PiP-venster (Picture-in-Picture) nadat één inhoud is afgespeeld, wanneer meerdere inhoud is geconfigureerd om te worden afgespeeld in de PiP.

**iOS TVSDK 3.6**

Geen nieuwe problemen in deze release.

**iOS TVSDK 3.5**

Geen nieuwe problemen in deze release.

**Versie 3.3**

(ZD#37820) - Toegevoegd staat plaatsing op de lijst voor aangepaste koptekst HS-ID, HS-SSAI-TAG toe.

**Versie 3.2**

* **Ticket#36588** - Er wordt een crash van de speler waargenomen wanneer de STOP-methode van MediaPlayer wordt aangeroepen.

Correctie van het periodiek vastlopen dat werd waargenomen wanneer de STOP-methode wordt aangeroepen voor een paar streams met ondertitels.

* **Ticket#37080** - Dubbele verzoeken die voor Duidelijke vraag worden gezien.
Oplossing voor de dubbele aanvragen voor Manifest-URL&#39;s tijdens het afspelen. TVSDK doet nu één vraag per manifest.

* **Ticket#37** - de normalisatieregel van CRS ontbreekt met eq gelijke typeFixed een geval waar de speler aan botsing gebruikte wanneer ontmoet met laatste normalisatieregel die voor hostnames met een &quot;eq&quot;gelijkenis wordt geplaatst.

**Versie 3.1**

**Ticket #36313** - Intermitterende onvoorspelbare resultaten tijdens Lineaire ad BreaksCorrectie afspelen met intermitterende tussenpozen tijdens lineaire en onderbrekingen in Live stream.

**Versie 3.0.1**

**Ticket36948** - CRS - Volgorde van de activaselectie inconsistent op iOS 12Het voor CRS geselecteerde middel is niet altijd de hoogste kwaliteitsvariant die in een reactie van VAST of VMAP wordt teruggegeven.

**Versie 3.0**

* **Ticket35311** - de status van de Speler wordt niet GEPAUZEERD tijdens een telefoongesprek interruptAdded onderbreekt manager om de speler tegen te houden die onderbreekt. Na onderbreking wordt de spelerstatus gepauzeerd en wordt het afspelen hervat wanneer u op de afspeelknop klikt.

* **Ticket36685** - Levende activa - De tijd wanverhouding met de vooruitgang van de spelertijd en de tijd van de tellertijd SCTE wordt berekend tijdCorrect voor de tellers SCTE die vóór live punt zijn.

* **Ticket36492** - `currentTime` en `localTime` worden niet bijgewerkt wanneer het zoeken naar een nieuwe positie tijdens gepauzeerde statusPlayer huidige tijd kan nu aan nul worden geplaatst voor het geval de speler in gepauzeerde staat is; eerder dan de huidige tijd die alleen in afspeelstatus op nul werd ingesteld.

**Versie 1.4.45**

* **Ticket36294** - iOS TVSDK werkt niet met Xcode 10Oplossing voor de compilatieproblemen met TVSDK op XCode 10. Vanwege de XCode 10-vereisten vereisen apps die op TVSDK voor iOS 1.4.45 en hoger bouwen, een minimaal implementatiedoel als iOS 7.0

* **Ticket36321** - Discrepancy waargenomen in het doorzoekbare bereik tussen `PTMediaPlayer` en `AVPlayer` bijvoorbeeld in de staat &quot;Afspelen&quot;.

* **Ticket36493** - `libstdc++` ondersteuning op iOS 12Fixed the compilation issues with TVSDK on iOS 12. Voor toepassingen die op TVSDK voor iOS 1.4.45 en hoger zijn gebaseerd, is een minimaal implementatiedoel vereist als iOS 7.0

**Versie 1.4.44**

* **Ticket34683** - Vooruitgang bij afspelen van advertenties verloopt negatief

Extra controles die worden uitgevoerd om het geval te behandelen wanneer er een wanverhouding tussen de duur die door de advertentieserver wordt gemeld en daadwerkelijke advertentie-inhoud is.

* **Ticket34801** - currentTime en localTime werden niet bijgewerkt toen het zoeken naar een nieuwe positie tijdens gepauzeerde statusPlayer huidige tijd kan nu aan nul worden geplaatst voor het geval de speler in gepauzeerde staat is; eerder dan de huidige tijd die alleen in afspeelstatus op nul werd ingesteld.

* **Ticket35037** - Playback stalls met slechte URL wanneer het terugkeren van op signaal-gebaseerd en toevoeging.
Verbeterde oplossing voor afgesloten uitgave #34385 in release 1.4.42. Toegevoegde isCanceled controle en uitzondering behandelende code om verrichtingsrij robuuster te maken.

**Versie 1.4.43**

* (ZD#32990) - iOS: Inhoud afspelen in plaats van advertenties op bepaalde actiepunten. `selectedMediaOptionInMediaSelectionGroup` API die deel uitmaakte van de AVPlayerItem-interface is nu verplaatst onder AVMediaSelection in iOS 11. Het probleem is opgelost met deze nieuwe API.

* (ZD#33683) TVSDK is verwijderd == achtervoegsel uit de metagegevenstekenreeksen. Het probleem is opgelost in de parseringslogica.

* (ZD#33905) - iOS TVSDK die vraag aan de manifestdossiers met twee gebruikersagenten maakt. Het probleem met de gebruikersagent is opgelost in de eerste m3u8-aanroep (nieuwbouw). M3u8&#39;s hebben nu dezelfde gebruiker-agenten voor alle aanroepen.

* (ZD#34293) - Pre-rolls die zijn ingevoegd in LINEAR-streams worden niet correct afgespeeld in iOS11. Het probleem is opgelost voor preroll-advertenties.

* (ZD#34684) - Wanneer het beleid voor het overslaan van advertenties wordt toegepast, worden Pre-roll en frames gedurende een paar seconden weergegeven. Er is een nieuwe API, enableVodPreroll, geïntroduceerd om het vooraf afspelen in het afspelen van wachtwoorden uit te schakelen. De standaardwaarde voor deze API is Ja. De API zorgt ervoor dat de inhoud van de hoofdinhoud wordt overgeslagen.

* (ZD#34765) - Na het aanroepen van stop() worden nog maar weinig transportstreamsegmenten gedownload. Verbeterde de Stop()-API om het downloaden van de extra segmenten te voorkomen.

* (ZD#34865) - Pre-roll advertenties voor livestream worden afgebroken op iOS. Dit probleem is opgelost. Dit probleem is verwant aan iOS11 en er wordt een extra controle toegevoegd om te controleren of de stream pre-roll of main-content is.

* (ZD#35093) - Oplossing voor een failover-scenario waarbij, als de Primaire variant van de stream bij het opstarten mislukt (404 wordt geretourneerd), het afspelen niet naar de back-upstream wordt geschakeld.

**1.4.42 (1.4.42.118)**

* (ZD#34385) - Afspeelstallen met een ongeldige URL bij het terugkeren van op signaal gebaseerde invoeging.

   Verhoog de maximum gezamenlijke tellingen voor `CustomAVAssetLoaderOperations`, zodat manifest kan blijven uitvoeren leest.

* (ZD#34373) - Eindgebruikers kunnen niet streamen naar met HDMI aangesloten apparaten wanneer het opnemen van streams wordt verboden.

* (ZD#32678) - TVSDK verzamelt de juiste id&#39;s voor advertenties niet op iOS.

   Advertentie-id van de uiteindelijke creatieve advertentie wordt nu opgenomen in VHL-pings in geval van omleiding van VAST/VMAP.

* (ZD#33904) - TVSDK is niet geregistreerd voor AVFFoundation-meldingen `AVAudioSessionMediaServicesWereLostNotification` en `AVAudioSessionMediaServicesWereResetNotification`.

   `PTMediaServicesWereLostNotification` en `PTMediaServicesWereResetNotification` kan nu worden geregistreerd in de Player-app om de meldingen op te halen wanneer de Media-services opnieuw worden ingesteld of verloren gaan.

* (ZD#33815) - Klanten kunnen hun regels voor prioritering en normalisatie van CRS niet bijwerken zonder een app-update te vereisen.

   De API&#39;s `getCRSRulesJsonURL` en `setCRSRulesJsonURL` API&#39;s zijn toegevoegd aan de TVSDK van iOS.

**Versie 1.4.41 (1.4.41.76)**

* (ZD #34464) - Issues building Reference App met TVSDK Version 1.4.41

   Als u deze versie start, is Xcode 9 vereist voor het compileren van TVSDK voor iOS.
* (ZD #29456) - Airplay start in de pauzestatus

   Het probleem met de pauze dat optreedt wanneer de video wordt gepauzeerd bij het invoeren van Airplay is opgelost.
* (ZD #30371) - De begintijd van AdBreak verandert wanneer wij meer dan twee advertenties in lineaire stroom opnemen

   Correctie van de fout bij het afspelen van inhoud op Apple TV, waardoor het afspelen niet volledig kon worden uitgevoerd.
* (ZD #32146) - Geen `PTMediaPlayerStatusError` ontvangen voor HLS Live-inhoud op het blokkeren van iOS 11 dev beta

   Er `PTMediaPlayerStatusError` wordt geen informatie ontvangen voor HLS Live- en VOD-inhoud bij het blokkeren met Charles (verbinding Slagen en 403).

* (ZD #29242) - Het afspelen van Airplay-video mislukt met advertenties ingeschakeld.

   Wanneer advertenties zijn ingeschakeld en AirPlay is ingeschakeld, wordt het afspelen van een video gestart, het afspelen van de video wordt nooit gestart en er wordt geen fout weergegeven.

* (ZD#33341) - `DRMInterface.h` triggers maken waarschuwingen in Xcode 9.

   Oplossing voor twee blokprototypen `DRMInterface.h` waarin het woord &#39;void&#39; in de parameterlijsten ontbrak.

* (ZD#31979) - Wordt niet gecompileerd/uitgevoerd als het iOS 10 of hoger is voor iPhone 7/iPhone7+.

   Correcte samenstelling van IB-documenten voor eerdere versies dan iOS 7 wordt niet meer ondersteund.

* (ZD#32920) - Leeg scherm binnen een Advertentiesonderbreking en geen Ad-onderbreking voltooiing.

   Wanneer een Ad-einde Ad-instanties weergeeft en nadat een advertentie-instantie is voltooid, wordt een leeg scherm weergegeven.

* (ZD#32509) - Schermopname van iOS 11 uitschakelen - Schermopname uitschakelen - schermopname uitschakelen in iOS 11.

* (ZD#33179) - Gebeurtenisfout met tussenpozen in iOS11.

   De gebeurtenisfout in iOS 11 is verholpen.

**Versie 1.4.40** (1.4.40.72)

* (ZD #32465) - Speler kan samengevoegde playlists niet behandelen.

   Bellen `finishLoadingWithError`(met: Fout) voor AV stichting om afwisselende stromen/trekker failover te proberen.

* (ZD #31951) - TVSDK-fout tijdens rotaties van licentie.

   Probleem met rotatie van licentie opgelost.
* (ZD #31951) - Leeg scherm binnen een Ad-einde en geen Ad-break-voltooiing.

   Behandelde een probleem waarbij Facebook VPAID-advertenties vaak meerdere CDATA-blokken in één `<AdParameters>` VAST-knooppunt retourneerden.
* (ZD #33336) - iOS TVSDK - Advertentiepods worden niet gevuld, ondanks dat er voldoende advertenties zijn geretourneerd door Freewieltje.

   Gemaakt bovenliggend-onderliggend verband tussen reeks en fallback en sorteren op basis van bovenliggende reeks en index.

**Versie 1.4.39** (1.4.39.43)

* (ZD #32178) - De versie van iOS TVSDK is onjuist.

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

Gebruik van Creative ID en AdSystem in CRS- verzoek dat op de normalisatieregels van CRS wordt gebaseerd.

* [ ZD #29462) - TremorHub en VOD voor A&amp;E waardoor iOS-apps vastlopen

**Versie 1.4.36 (1.4.36.835)**

* (ZD #29418) - In telefoons met duur 0 (#EXT-X-CUE-OUT:0.000) wordt het afspelen gestopt of vastgelopen door iOS TVSDK.

Het probleem is opgelost en het afspelen wordt op de juiste wijze gestart.

* (ZD #29462) - Advertentie bij VOD die ertoe leidt dat de TVSDK van iOS vastloopt.

Het probleem is opgelost. De iOS-TVSDK verhoogt en verwerkt dit `exception(AUDNetworkAdInfo::initWithAdId)` niet. De uitzondering wordt veroorzaakt door een lege advertentie-ID.

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

Voor een FER-stream wordt de toets voor het ad-einde ingevoegd na het einde van het ad-einde. Dit probleem is opgelost door de *laatst weergegeven toets* aan het einde van het advertentiespoor toe te voegen.

**Versie 1.4.33** (1.4.33.803 voor iOS 6.0+)

* (ZD# 21701) CRS inschakelen voor subrekeningen

Ingeschakeld door de oorspronkelijke creatieve URL voor de 1401 CRS-aanvraag te verzenden in plaats van de genormaliseerde URL, volgens de vereiste voor CRS-back-end.

* (ZD# 26218) - Laadprobleem PSDKResources.bundle

Dit probleem is opgelost door het laden van bronnen bij te werken en uit alle beschikbare bundels te zoeken.

* (ZD# 27460) eerste vraag van Midroll - POST aan het `cdn.auditude.com` terugkeren van 403.

De nieuwe CDN-account kan een POST CDN-aanvraag niet verwerken. Dit probleem is opgelost door de code bij te werken en het `cdn.auditude.com` advertentieverzoek in te dienen om GET in plaats van POST te zijn.

**Versie 1.4.32** (1.4.32.792 voor iOS 6.0+)

* (ZD# 27132) Ondersteuning voor decimale waarden voor VMAP Ad Breaks.

Wanneer de inhoud niet langs de gedefinieerde ad-hocafbrekingen werd gesegmenteerd, veroorzaakten gehele getallen onverwachte ad-positionering. Het probleem is opgelost door de decimale waarden niet om te zetten in gehele getallen.

* (ZD# 27189) AES-inhoud met de EXT-X-DISCONTINUITY-SEQUENCE-tag wordt niet correct afgespeeld.

Het probleem is opgelost door de tag aan het begin van de afspeellijst te plaatsen.

**Versie 1.4.31** (1.4.31.785 voor iOS 6.0+)

* (ZD# 24528) Gebruikswaarden voor TVSDK implementeren voor facturering

Zie [Factureringscijfers]voor meer informatie.

* (ZD# 24642) Picture-in-Picture support for TVSDK

De functie beeld-in-beeld, die in sommige gevallen niet goed werkte, is gecorrigeerd.

* (ZD# 25246) Onjuiste e-mails

Dit probleem is opgelost door discontinuïteitscodes op verschillende manifests uit te lijnen.

* (ZD# 26218) Het ontwikkelen van de toepassing wordt gecompliceerd bij het opnemen van PSDKLibrary.framework in het toepassingsframework van de client

Dit probleem is opgelost door het PSDKLibrary.framework in te pakken zoals gevraagd.

* (ZD# 26364) Ondersteuning voor meerdere CDN&#39;s voor CRS-advertenties

Zie Meerdere CDN-ondersteuning voor CRS en levering voor meer informatie.

* (ZD# 27028) Vertraging bij het afspelen van sommige streams in iOS 10.

Dit probleem is opgelost door een oplossing te bieden voor streams die geen M3U8-extensie hebben.

**Versie 1.4.30** (1.4.30.754 voor iOS 6.0+)

De volgende problemen zijn in deze release opgelost voor TVSDK:

* (ZD# 24180) Voeg een aangepaste koptekst toe om lijst toe te staan.

Er is een nieuwe aangepaste koptekst toegevoegd aan de lijst voor TVSDK-toestaan.

* (ZD# 25016) Failover-stroom wordt willekeurig geselecteerd wanneer ABR-besturingsparameters worden ingesteld

Dit probleem is opgelost door de ABR-streams op volgorde te houden wanneer de ABR-instellingen de initialBitrate-instelling krijgen voor een stream die failover-URL&#39;s bevat. Hierdoor wordt het afspelen van de failover-streams in plaats van primair vermeden.

* (ZD# 25076) Crash on PTAuditudeAdResolver loadComplete

Het probleem waarbij een crash optrad tijdens het snel starten/stoppen van meerdere PTMediaPlayer-instanties met advertenties is opgelost.

* (ZD# 25960) Geen extra ingetekende markeringen die het bericht van de meta-gegevensverandering teweegbrengen uitzendingen

De kwestie waar een geabonneerde markering niet wordt meegedeeld wanneer het verschijnt alvorens het eerste segment in manifest is bevestigd.

* (ZD# 26084) PSDK met 106000,101000.-11833-decoder heeft geen fout aangetroffen bij het overschakelen van de laatste en het afbreken naar entertainmentinhoud

Wanneer de laatste begintijd van de advertentie-break van de VMAP valt voordat de totale duur is voltooid, wordt in bepaalde omstandigheden de toets pas ingevoegd na het einde van het laatste ad-break. Dit probleem is opgelost.

* De videokaart (VHL) is bijgewerkt naar versie 1.5.9 om de volgende problemen op te lossen:

* (ZD #22351) VHL - Analytics: Duur van live video-element

Dit probleem is opgelost door de API voor assetDuration aan PTVideoAnalyticsTrackingMetadata toe te voegen om de duur van de elementen voor Live/Lineaire streams bij te werken en een logica te bieden voor het controleren van de live stream.

* (ZD# 22675) VHL - Analytics: De duur van live video-elementen bijwerken

Dit probleem is hetzelfde als ZD #22351.

* (ZD #25908) VHL - Analytics: Adobe Hartslaggebeurtenis vastloopt

Dit probleem is opgelost door de implementatie bij te werken en de nieuwste versie van VHL voor iOS versie 1.5.9 te gebruiken om de stabiliteit en prestaties te verbeteren.

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

De steun voor douanekopballen op zijn segmentverzoeken door de klasse PTNetworkConfiguration is toegevoegd.

**Versie 1.4.28** (1.4.28.722)

* (ZD #24549) Veelvoudige en volgende vraag

Dit probleem is opgelost door het tijdlijnbeheer bij te werken en te luisteren naar meldingen over een specifiek object wanneer meerdere spelers zijn gemaakt.

* (ZD #24758) PTManifestLogger biedt geen ondersteuning voor iOS 8

Dit probleem is opgelost door de logger-hulpprogrammabibliotheek bij te werken naar het implementatiedoel voor versie 7.0.

* (ZD #24775) Vertraagde stream vanwege advertenties

Dit probleem is opgelost door de tijdsverloop op afspeellijsten van gebeurtenissen correct te berekenen.

* (ZD #24799) Sommige afleveringen worden niet afgespeeld op iOS APP

Dit probleem is opgelost door de lokale webserver te gebruiken voor ondertitels wanneer de WebVTT-bestanden beperkt zijn.

**Versie 1.4.27** (1.4.27.711) voor iOS 6.0+

* (ZD #24089) - Optimalisaties voor en oplossingen voor lange DVR-streams

Dit probleem is opgelost door meerdere optimalisaties toe te voegen om de tijd te verminderen die nodig is om het DVR-venster in live/lineaire streams te verwerken.

* (ZD #21554) - Foutbeacons voor TVSDK die niet zijn geactiveerd voor het toepassingstype = video/mp4

Dit probleem is opgelost door de speler in staat te stellen de juiste URL&#39;s voor het bijhouden van fouten op ongeldige elementindelingen te pingelen.

* (ZD #24424) - Crash van het type EXC_BAD_ACCESS KERN_INVALID_ADDRESS komt van binnen PSDKLib voor iOS op nieuwere hardwareapparaten.

De crash die optrad als gevolg van een niet-toegewezen instantie van de mediaspeler, waarbij het afspelen snel tussen verschillende streams wordt geschakeld, is opgelost.

* (ZD #24575) - Crash in TVSDK op 32-bits apparaten wanneer enableDebugLog=true

De kwestie in het logboekformaat dat de botsing op apparaten met 32 bits veroorzaakte wanneer het registreren wordt toegelaten is opgelost.

**Versie 1.4.26** (1.4.26.702) voor iOS 6.0+

* (ZD# 20213) - TVSDK FW moet dynamisch/gemoduleerd zijn voor XCode7

De bibliotheken zijn bijgewerkt met ondersteuning voor modules.

**Versie 1.4.25** (1.4.25.684) voor iOS 6.0+

* (ZD #19629) - Live video wordt gepauzeerd bij het betreden van Airplay naar ATV 4

Dit probleem is opgelost door een wachttijd toe te voegen na het verwijderen van oude items, maar voordat u nieuwe items toevoegt aan de AVQueuePlayer. Zonder de wachttijd worden meldingen verzonden naar het onjuiste object.

* (ZD #19856) - Geen ondertitels worden weergegeven wanneer deze standaard zijn ingeschakeld

De problemen in de webvtt-afspeellijst, waardoor de ondertitels niet correct werden weergegeven, zijn opgelost.

* (ZD #21590) - Videoprestaties en tracering in de nieuwste Origin Builds

Het probleem met de ontbrekende videolengte in VideoAnalytics is opgelost.

* (ZD #20202) - De iOS-app loopt vast door aangepaste opmaakstijlen voor ondertitels in te stellen

Dit probleem is opgelost door extra null-objectcontroles toe te voegen tijdens het instellen van ondertitelingsstijlen.

* (ZD #20709) - videolengte gerapporteerd als 0 in video start tracking

Dit probleem is hetzelfde als (ZD #21590).

* (ZD #22280) - Analytics Video Length wordt ingesteld op 0

Dit probleem is hetzelfde als (ZD #21590).

* (ZD #22592) - Problemen met Airplay in Primetime

Dit probleem is hetzelfde als (ZD #19629).

* (ZD#22922) - Handmatige bitsnelheidomschakeling voor iOS

Dit probleem is opgelost met een optie voor het opgeven van de maximale bitsnelheid.

* (ZD #23084) - Apple-compatibiliteit voor IPv6-netwerken

De symbolen die niet door Apple werden aanbevolen voor IPv6-compatibiliteit zijn verwijderd.

**Versie 1.4.24** (1.4.24.661) voor iOS 6.0+

* ZD #2548) - Primetime ondersteuning voor interactieve reclame op mobiele apparaten - VPAID 2.0

Dit probleem is opgelost door de logica bij te werken om de weergave van de speler weer te geven als een VPAID-advertentie niet wordt afgespeeld.

* (ZD #20101) - Bij de implementatie van Aangepast hoofdstuk wordt de gebeurtenis start van het hoofdstuk tijdens het afspelen van het document geactiveerd

Dit probleem is opgelost door VideoAnalyticsTracker bij te werken om het begin/einde van een hoofdstuk correct te detecteren bij het schakelen tussen grenzen van hoofdstukken en niet-hoofdstukken.

* (ZD #20784) - Analytics: Het triggeren van inhoud wordt voltooid voor live video-overgangen

Dit probleem is opgelost door een logica toe te voegen die handmatig het voltooien van de inhoud tijdens een sessie voor het bijhouden van video activeert.

De volgende bibliotheken zijn bijgewerkt:

* AdobeMobile-bibliotheek naar 4.10.0
* VHL-bibliotheek naar 1.5.6
* VHL-Nielsen-bibliotheek naar 1.6.7
* (ZD #21855) - Ondertitels worden niet afgespeeld na de middelste rol

In dit geval leidden dubbele discontinuïteitslabels ertoe dat ondertitels niet na de middelste rol werden weergegeven. Dit probleem is opgelost door de volgende discontinuïteitscodes te verwijderen.

* (ZD #21994) - Tekenreeks buiten de grenzen in PTHLSUtils

De meest waarschijnlijke oorzaak van de botsing is wanneer een EXT-x-SLEUTEL een URL heeft die door citaten wordt omringd.

* ZD #22074) - AUDVAST crasht eenmaal per minuut op iOS

In versie 1.4.23 is de crash hersteld die werd veroorzaakt door de aanwezigheid van onveilige tekens in een VAST-URL voor omleiding. TVSDK bleef deze advertenties echter overslaan.

Dit probleem is opgelost door de onveilige tekens te verwerken en de advertenties af te spelen.

* (ZD #22694) - PTMediaPlayer.  Weergave is verborgen voor speler

Dit probleem is opgelost door de logica bij te werken om de weergave van de speler weer te geven als een VPAID-advertentie niet wordt afgespeeld.

**Versie 1.4.23** (1.4.23.641) voor iOS 6.0+

* (ZD #18016) - Geen reactie van Primetime SDK met een slechte netwerkvoorwaarde

Dit probleem is opgelost door het foutbericht te verbeteren wanneer een fatale fout van AVFFoundation optreedt en de toepassing toe te staan het opnieuw opstarten af te handelen na de fout.

* (ZD #20580) - Crash in PTSplicerManager

Dit probleem is opgelost door extra bescherming te bieden tegen gelijktijdige problemen die de crash veroorzaken.

* (ZD #21782) - iOS-foutcode 10100

Het probleem waarbij de TVSDK een fout van 101000 heeft geretourneerd bij het starten van het afspelen op Adobe Access DRM-streams is opgelost.

* (ZD #21889) - Onlineadvertenties en het afspelen van offline inhoud mislukt

Het probleem waarbij het afspelen mislukte nadat een advertentie met met AES gecodeerde offline inhoud was opgelost.

* (ZD #22074) - AUDVAST crasht eenmaal per minuut op iOS

Dit probleem is opgelost door de verwerking van VAST-tags van derden met ongeldige tekens in de URL te verbeteren.

* (ZD #22257) - De TVSDK kan de DRM-stream niet afspelen

Het probleem waarbij de TVSDK die een fout van 101000 heeft geretourneerd terwijl het afspelen werd gestart op Adobe Access DRM-streams, is opgelost.

**Versie 1.4.22** (1.4.22.627) voor iOS 6.0+

* (ZD #18709) - Crash in de TVSDK voor iOS

Het probleem met een crash die optreedt bij bepaalde met Adobe Access DRM beveiligde streams is opgelost.

* (ZD #18850) - Creatieve selectielogica bijwerken op basis van CRS-regels

Dit probleem is opgelost door een .json-configuratiebestand toe te voegen waarin de prioriteit voor creatieve selectie wordt opgegeven.

* (ZD #19770) - Beveiligde AES-videofeed wordt niet meer afgespeeld

Het probleem waarbij bepaalde 302 omgeleide stromen niet speelden, is opgelost.

* (ZD #19629) - Live video wordt gepauzeerd bij het betreden van Airplay naar ATV 4

Dit probleem is opgelost door een tijdelijke oplossing toe te voegen voor het onderbreken van live video wanneer airplay is ingeschakeld voor Apple TV 4-apparaten. Het probleem lijkt een AppleTV 4-probleem te zijn.

* (ZD #21119) - De TVSDK wordt na het afspelen van de advertentie gestopt

Er is ondersteuning toegevoegd voor met AES gecodeerde streams met een reeks IV tijdens het gebruik van een invoegtoepassing.

* (ZD #21125) - Terugkeer van begin van leven/lineair en break

Er is ondersteuning toegevoegd voor het retourneren van een advertentie-einde vroeg voordat het advertentieeinde wordt afgespeeld. De vroege terugkeer wordt vermeld door een markering van douanemanifest.

* (ZD #21224) - Airplay-ondersteuning voor verdeelde streams van Akamai

API&#39;s zijn toegevoegd aan de klasse PTNetworkConfiguration om cookies toe te voegen als URL-parameters op segmenten voor bepaalde Akamai-tokenized streams.

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

Dit probleem is opgelost door een time-outgebeurtenis (requestTimeout) op te geven aan de toepassing en de adMetadata.  adRequestTimeout-API om de standaardtime-out van 10 seconden te overschrijven.

* (ZD #19446) - Melding ontbreekt voor Live streams

Dit probleem is opgelost door toe te staan dat de toepassing zich abonneert op de EXT-X-PROGRAMM-DATE-TIME voor live streams.

* (ZD #19459) - Crash bij het voorbereiden van alternatieve audio met PTMediaPlayerItem prepareAudioOptionsWithAVMediaSelectionOptions
* (ZD #19460) - Crash - `[PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]`

Dit is hetzelfde als Zendesk #19459.

* (ZD #19574) - De TVSDK retourneert geen M3U8-responsgegevens voor DRM- of niet-DRM-inhoud

Als het laden van het manifestbestand in PTMediaPlayerItem.prepareToPlay is mislukt, rapporteert de TVSDK de hoofdtekst van de mislukkingsreactie op de toepassing niet.

Dit probleem is opgelost door de TVSDK toe te staan de mislukkingsreactie als een fout aan de toepassing te melden.

* (ZD #19615) - Back-uplogica werkt niet

In de huidige implementatie zijn fallback-advertenties overgeslagen en niet opnieuw verpakt, tenzij deze advertenties de indeling m3u8 hebben. Dit probleem is opgelost door ook ondersteuning toe te voegen voor het opnieuw verpakken van fallback-advertenties.

* (ZD #19770) - De TVSDK kan geen beveiligde AES-inhoud afspelen met 302 omleiding

Het omleidingsprobleem is opgelost, omdat de omleidings-URL werd weggevaagd door cleanConnectionData voordat het kon worden gebruikt om het manifest te parseren.

* (ZD #19856) - Ondertitels worden niet voor sommige bitsnelheden weergegeven als dit standaard is ingeschakeld

Dit probleem is opgelost door de fout van iOS af te handelen voor de segmenten van de streams waarin de ondertitels niet worden weergegeven.

* (ZD #19868) - De TVSDK loopt vast als een ongeldige creatieve persoon wordt verhandeld

De crash in de TVSDK waarbij een instantie van de grote parser onjuist werd afgehandeld, is opgelost.

* (ZD #20180) - VPAID-advertenties worden af en toe overgeslagen

JavaScript-mime-type werd niet altijd opgenomen of beschouwd als een geldig mime-type. Dit probleem is opgelost door JavaScript op te nemen als een geldig MIME-type.

* (ZD #20749) - Bij fallback worden niet-lege VAST-reacties overgeslagen; URL&#39;s met extra URL&#39;s en tekstspatiëring worden geactiveerd

De kwestie waar sommige van de creatieve producten niet opnieuw worden verpakt, is opgelost.

**Versie 1.4.19** (1.4.19.563) voor iOS 6.0+

* ZD #18639) - De TVSDK gebruikt buitensporige CPU/bronnen op een langdurig opnameapparaat

Dit probleem is opgelost door de DRM m3u8-afspeellijst te optimaliseren en te herschrijven naar cachebits van de afspeellijst die eerder zijn herschreven. Dit is het meest relevant wanneer u live m3u8-streams afspeelt waarvoor de m3u8 wordt gedownload na elke segmentdownload.

* (ZD#18956) - player.drmManager is nul wanneer het onderbrekingspunt is ingesteld in iOS Demo Player

Dit probleem is opgelost door de PTMediaPlayer.drmManager API-implementatie bij te werken en DRMManager op te halen uit het DRM-framework.

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

* (Zendesk #3304) - VAST 3.0- `[ERRORCODE]` macro niet gevuld

Het probleem waarbij de Auditude SDK er niet in slaagt te verzenden pingelt wanneer volgende URL ruimten aan het begin heeft is opgelost.

* (Zendesk #17294) - Crash SecKeyRawSign

Een mogelijke crash wanneer de code van de klant de sleutelketen gebruikt is opgelost.

* (Zendesk #18008) - Ondersteuningscookies voor iOS8+ voor ondersteuning van gebonden streams

Voor speciaal voor Akamai geoptimaliseerde streams is het vereist dat cookies worden verzonden bij verzoeken van segmenten. Dit was niet mogelijk in iOS 7 en eerder. Apple heeft vanaf iOS 8 een API toegevoegd waarmee cookies kunnen worden doorgegeven voor segmentaanvragen. Deze ondersteuning is nu beschikbaar in de TVSDK. Er is ook ondersteuning toegevoegd voor het verzenden van een gebruikersagent, indien beschikbaar.

* (Zendesk #18166) - TVSDK 1.4.15 geeft honderden waarschuwingen wanneer u compileert met DWARF met dSYM-bestandsopties

Alle waarschuwingen zijn opgelost.

**Opmerking**: Er zijn tvOS-compatibele bibliotheken toegevoegd voor TVSDK.

**Versie 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Tab S loopt vast tijdens het afspelen

Het terugkeren van de afhankelijkheid van OKHTTP op controle voor CRS omdat TVSDK nu de httpurlconnection in plaats van curl direct gebruikt. Het probleem werd opgelost door uitzonderingen te verhelpen voordat een nieuwe JNI-oproep werd gedaan.

* (Zendesk #4487) - Lineair kanaal van inhoud volgen

Het probleem is opgelost door de videohartslagtracker tijdens een lineaire streamafspeelsessie opnieuw te initialiseren.

* (Zendesk #17919) - Android - bij het zoeken naar inhoud treedt een hartslagfout op

Het probleem was om de hartslag in een foutenstaat op te lossen wanneer er een vraag in een hoofdstuk is

* (Zendesk #18053) - Toepassing met de TVSDK-crash bij Marshmallow

De TVSDK liep vast op Android M OS toen de TVSDK-bibliotheek neoncode gebruikt die YUV `->` RGB-kleurconversie uitvoert. Dit probleem is opgelost door de functies die dit probleem veroorzaken bij te werken met een niet-neonversie van `code`.

* (Zendesk #18072) - Android M - Toepassing vastloopt

Deze crash gebeurt tijdens het aanroepen van de API&#39;s MediaCodecList en MediaCodecInfo wanneer wordt gecontroleerd of het profiel en het niveau worden ondersteund. Adobe zoekt naar ondersteuning van Google voor meer inzicht. Dit probleem is opgelost door een tijdelijk probleem op te lossen door alle codec-informatie van tevoren te laden, zodat deze API&#39;s niet alleen hoeven te worden aangeroepen wanneer codec-informatie nodig is.

* (Zendesk #18074) - Arabische ondertitels die niet werken op Nexus met Android 6.0

Dit probleem is opgelost door ondersteuning te bieden voor de Android CTS-lettertypetoewijzing.

**Versie 1.4.15** (1.4.15.512) voor iOS 6.0+

**Opmerking**: De Nielsen-module is verwijderd uit de TVSDK-build, maar de TVSDK wordt in de nabije toekomst bijgewerkt met een nieuwe Nielsen-integratiemodule.

* (ZD #2228) - Fout die van het halen van manifest niet beschikbaar in MediaPlayerNotification is teruggekeerd

Toegevoegde metagegevens om inhoud beschikbaar te maken wanneer de melding M3U8_PARSER_ERROR plaatsvindt.

* (ZD #4437) - Crashes in Adobe Primetime SDK

Probleem verholpen waarbij het programma vastloopt tijdens het voorbereiden van ondertitels/alternatieve audio.

* (ZD #4487) - Lineair kanaal van inhoud volgen

Herinitialisatie van de videohartslagtracering is toegestaan tijdens een lineaire streamafspeelsessie.

**Versie 1.4.14** (1.4.14.498) voor iOS 6.0+

* (ZD #17260) - Crash on playlistManagerForURL

Probleem verholpen waarbij een periodiek crash optrad als gevolg van gelijktijdige uitvoering.

**Versie 1.4.13** (iOS 6.0+)

* (ZD #3304) - VAST 3.0- `[ERRORCODE]` macro niet gevuld

   * Foutcode 400 wordt weergegeven als deze inline is en slecht creatief is.
   * `[ERRORCODE]` macro wordt URL-gecodeerd.

* (ZD #3865) Integratie van hartslag met IMA-advertenties

Het probleem waarbij de videolengte onjuist werd gerapporteerd, is opgelost.

* Bijgewerkte TVSDK-demospeler voor ondersteuning van iOS 9

Om iOS 9 behoorlijk te steunen, moet u de uitzonderingen van de Veiligheid van het Vervoer van de Toepassing vormen. Voor de demo is het ATS volledig uitgeschakeld.

**Versie 1.4.12** (1.4.12.464) voor iOS 6.0+

* (ZD #4521) CRS Testing Client Side and SSAI

Correctie van onjuiste reverse MD5 in 3P URL.

**Versie 1.4.12** (1.4.12.463) voor iOS 6.0+

* (ZD #2751) CSAI en CRS / Verbeteren: Dynamische elementen in bepaalde URL&#39;s van mediabestanden verwerken.

Bijgewerkte Creative Repackaging Service voor het correct verwerken van advertenties met dynamische creatieve URL&#39;s.

* (ZD #3654) Geheugenlek in PSDK-versie na 1.3.4.166

Herstel van geheugenlek in drmFramework met regelmatig afspelen op iOS 8.2-apparaten

* (ZD #3988) Preroll wordt overgeslagen wanneer het zoeken terug in het na eerste playback

Oplossing van een bug zodat advertentiebeleid correct kon worden uitgeschakeld.

* (ZD #4017) Een iOS API aanvragen om af te spelen en te forceren op achterwaarts zoeken

Opgelost met fix voor ZD #4279

* (ZD #4279) HLS TVSDK en invoeging -302 redirect issue on iOS and Desktop

Het probleem waarbij een advertentie-element gebruikmaakte van een relatieve omleiding naar de URL, is opgelost.

**Versie 1.4.9** (1.4.9.427) voor iOS 6.0+

* (ZD #3075) Internet Reachability Issue - iOS

Er is een melding toegevoegd om te detecteren wanneer het afspelen is gestopt.

* (ZD #3193) Verzoek om een API voor profielwijziging in TVSDK

Bijgewerkte PTPlaybackInformation om bijgewerkte indicatedBitrate bloot te stellen. Bijgewerkte BITRATE_CHANGE-melding om betrouwbaarder en nauwkeuriger te zijn voor de M3U8 rapporteerde bitsnelheden.

* (ZD #3324) Primetime advertenties die een probleem melden als er geen advertentiemedia in VMAP zijn

Door TVSDK worden lege URL&#39;s voor het bijhouden van regeleinden en afbrekingen ondersteund en worden de begin- en eindinstellingen voor lege advertentie-einden gecontroleerd.

**Versie 1.4.8** (1.4.8.402)

* (ZD #3158) IOS 7 crasht in Volledige Replay van de Gebeurtenis

**Versie 1.4.7** (1.4.7.382)

* (ZD #2197) Fouten opvolgen en opsporen. Toegevoegde melding voor element kan manifest niet laden.
* (ZD #2894) Player maakt 4 manifestverzoeken op hoofdniveau tijdens het afspelen.
* (ZD #2992) Auditude Reporting rare duration and identifiers.

**Versie 1.4.6**(1.4.6.325)

* (ZD #2197) Fouten opvolgen en opsporen. Toegevoegde melding voor element kan manifest niet laden

**Versie 1.4.5** (1.4.5.283)

* (ZD #2141) Analytics-implementatie voor de TreeHouse-app, met bibliotheek toegevoegd om het pakket samen te stellen. `AdobeAnalyticsPlugin.a`
* Video Heartbeats Library update naar 1.4.1.2
* [PTPALY-4226] [verwant aan ZD #2423) Het uitvoeren van het Terugstellen DRM kan in schrapping van de gegevens van het Document van de Toepassing resulteren.

**Versie 1.4.4** (1.4.4.242)

* Video Heartbeats Library (VHL)-update naar 1.4.1.

* (ZD #2435) TV SDK-documentatie over analysemogelijkheden moet worden bijgewerkt

**Versie 1.4.2** (1.4.2.210 : iOS 6.0+)

* (ZD #1129) leeg `_player.currentItem.audioOptions` retourneren
* (ZD #2109) Primetime PSDK 1.4.1.125 werkt niet met Xcode 5.1.1
* (ZD #2137) Crash in PSDK op iOS wanneer DRM-metagegevens niet kunnen worden geladen

**Versie 1.4.1**(1.4.1.125)

* (ZD #1107) CocoaLumberjack duplicate symbols
* (ZD #1644) iOS-gebruikersagent wijzigen voor doelen en rapportage
* (ZD #1850) Cacao Lumberjack files included in iOS SDK
* (ZD#1908) Aangepaste tags worden genegeerd door PSDK als er meer dan 1 is

**Versie 1.4.0** (1.4.0.32)

* Zendesk #1024 - Functie voor het verwijderen van advertenties uit de stream via manifest

## Apparaatcertificering en ondersteuning {#device-certification-and-support}

>[!NOTE]
>
>De volgende functies worden **niet** ondersteund in de TVSDK:
>
>* Trage beweging op elk platform of elke versie.
>* Live truc.


**Versie 1.4.43**

* TVSDK 1.4.43 is gecertificeerd voor iOS 11.

**Versie 1.4.29**

* TVSDK 1.4.29 is gecertificeerd voor iOS 10.

**Versie 1.4.28**

* TVSDK 1.4.28 is gecertificeerd voor iOS 10 Beta 7.
* DRM-ondersteuning om HTTPS te forceren door API&#39;s `forceHTTPS` en `isForcingHTTPS` API&#39;s toe te voegen.
* Bijgewerkte VHL-bibliotheken naar 1.5.8, Adobe Mobile-bibliotheken naar 4.8.4 en de logger-hulpprogrammabibliotheek naar het doel voor implementatie van versie 7.0.

**Versie 1.4.19**

Deze versie van de TVSDK is gecertificeerd met de FairPlay-ondersteuning voor iOS en tvOS.

**Versie 1.4.17**

* tvOS

   Deze versie van de TVSDK biedt ondersteuning voor tvOS en is gecertificeerd voor niet-gecodeerde HLS-streams.

   **Opmerking**: Houd rekening met de volgende compilatierichtlijnen:

   * De TVSDK-tvOs-ondersteuning is beperkt tot niet-Adobe DRM-gecodeerde streams. U moet de verwijzing naar drmNativeInterface.framework verwijderen in uw tvOS-ontwikkelinstellingen. Met AES gecodeerde stromen worden nog steeds ondersteund.
   * Apple eist dat alle Apple TV-toepassingen zijn ingeschakeld voor bitcode. U moet deze markering dus in de projectinstellingen inschakelen.

## Bekende problemen en beperkingen {#known-issues-and-limitations}

* Vanwege de afgekeurde iOS UIWebView-klasse, vanaf iOS TVSDK 3.6:
   * VPAID-advertenties worden niet afgespeeld zoals wordt verwacht in iPad 13.
   * Companion-advertenties spelen niet zoals verwacht.

* In iOS TVSDK worden alle advertenties vastgezet in het inhoudsmanifest. Advertentiepatronen worden geïmplementeerd door te zoeken op basis van de duur van de inhoud en advertentiesegmenten. Dus als de duur van het segment niet nauwkeurig is, eindigt het zoeken mogelijk niet altijd bij het exacte frame van het begin of einde van het advertentiespoor. Zelfs als de duur van het frame beperkt is, is er een tolerantie die het platform zelf oplegt aan zoeken. Er kunnen enkele frames of advertenties of inhoud worden weergegeven. Dit is een beperking van het platform en de manier waarop en de invoeging werkt met TVSDK op iOS.
* Het besluit om over te slaan gebeurt in dit geval op de gebeurtenis seek. Aangezien de tijdsduur van het advertentiesegment in het manifest echter de werkelijke duur van de advertentie niet nauwkeurig vertegenwoordigt, is de zoekactie niet nauwkeurig. U ziet dus een paar frames advertentie wanneer het advertentiebeleid wordt toegepast.
* Het kan voorkomen dat tijdens het roteren van licenties de video niet wordt afgespeeld op iOS 11 en dat deze goed wordt afgespeeld op iOS 9.x en iOS 10.x.
* Als bij VPAID 2.0-ondersteuning het afspelen via AirPlay actief is, worden VPAID-advertenties overgeslagen.
* Het drmNativeInterface.framework is niet correct gekoppeld wanneer het minimumdoel is ingesteld op iOS7 (of hoger).
Oplossing: Geef expliciet de bibliotheek libstdc+.6.dylib op als volgt: Ga naar Target->Build Phases->Link Binary with Libraries en voeg libstdc++.6.dylib toe.
* Post-Roll Advertentie wordt niet ingevoegd voor vervangings-API.
* Als u een advertentie-einde zoekt (zonder er uit te komen), wordt een dubbel advertentie-begin- en advertentierapport weergegeven
* Het instellen van currentTimeUpdateInterval heeft geen effect.
Opmerking: In bepaalde iOS-versies laadt het besturingssysteem niet automatisch de bronnen in het PSDKLibrary.framework. Het is belangrijk om PSDKResources.bundle aan de bundelmiddelen van de toepassing manueel te kopiëren: Ga naar &quot;Build Phases&quot; en kopieer bundelbronnen.
* De Reference App kan niet worden samengesteld met behulp van Xcode 8 of lagere versies. vanaf iOS TVSDK versie 1.4.41, gebruik Xcode 9 om te compileren.
* VPAID-advertenties voldoen niet aan de waarde delayAdLoadingTolerance.
* 24077- Voor bepaalde HLS-inhoud met ondertitels loopt de speler vast bij de methode Stoppen of Herstellen.
* Gedetailleerde foutmeldingen zijn niet beschikbaar als Just in Time Ad resolving is ingeschakeld.
* Foutmeldingen worden geregistreerd volgens de tijd van de advertentieresolutie en niet volgens de volgorde van de advertentie.
* HEVC-ondersteuning heeft de volgende beperkingen in deze release
   * DRM wordt niet ondersteund
   * CC-ondersteuning (CEA 608/708) is niet beschikbaar omdat deze niet wordt ondersteund in CMAF.
   * 4K-ondersteuning is nog niet aanwezig.
   * ID3-tags worden niet ondersteund, omdat deze niet worden ondersteund in CMAF.
   * Niet-gedempte live HEVC-streams zijn niet geverifieerd.
   * Ondersteuning voor HEVC-advertenties is niet geverifieerd.
* Als JIT ingeschakeld is en de tolerantie op 10 seconden is ingesteld, wordt geen VAST-aanroep gezien voor de eerste midroll en break in het geval van VMAP->VAST-omleidingsadvertenties.
* Wanneer de time-out bij de resolutie van de advertentie correct werkt, verwacht de speler telkens wanneer de afspeellijst wordt bijgewerkt tijdens het afspelen van live stream een vastgezette afspeellijst binnen 20 seconden. Als er binnen het genoemde interval geen vastgezette afspeellijst wordt ontvangen, wordt een interne fout gegenereerd en wordt de speler gestopt.

## Nuttige bronnen {#helpful-resources}

* [TVSDK 3.4 voor iOS-programmeergids](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-for-ios/introduction/ios-3x-overview.html)
* [Referentie voor TVSDK iOS 3.4 API](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v34/index.html)
* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html) .
