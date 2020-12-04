---
title: Opmerkingen bij de release TVSDK 1.4 voor desktop HLS
seo-title: Opmerkingen bij de release TVSDK 1.4 voor desktop HLS
description: TVSDK voor Desktop HLS de Nota's van de Versie beschrijven wat nieuw of veranderd is, de opgeloste en bekende kwesties in TVSDK DHLS.
seo-description: TVSDK voor Desktop HLS de Nota's van de Versie beschrijven wat nieuw of veranderd is, de opgeloste en bekende kwesties in TVSDK DHLS.
uuid: 84da27b7-299b-478d-88f5-ef943f0a8321
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: e4437a26-9454-4da1-ae87-0fce664aac3d
translation-type: tm+mt
source-git-commit: ba291a4615a8e0713cf610f76f41e328da96ec4d
workflow-type: tm+mt
source-wordcount: '5222'
ht-degree: 0%

---


# TVSDK 1.4 voor Opmerkingen bij de release van Desktop HLS {#tvsdk-for-desktop-hls-release-notes}

De Nota&#39;s van de Versie van TVSDK voor Desktop HLS beschrijven wat nieuw of veranderd, de opgeloste, en bekende kwesties in TVSDK DHLS is.

## Nieuwe functies {#new-features}

**1.4.31.**

* **Ondersteuning voor meerdere CDN&#39;s voor CRS-advertenties**

   * Standaard worden alle getranscodeerde elementen gehost op een CDN die eigendom is van een Adobe op Akamai. Met de nieuwste release biedt de Adobe Creative Repackaging Service (CRS) u de mogelijkheid om de getranscodeerde creatieven te uploaden naar meerdere CDN&#39;s, zoals opgegeven door de klant.
   * Nieuwe API&#39;s worden toegevoegd aan TVSDK om het opgeven van de uiteindelijke creatieve CRS-URL mogelijk te maken wanneer de standaard-URL niet wordt gebruikt. Raadpleeg de documentatie voor meer informatie over het gebruik van deze nieuwe API&#39;s.

### Nieuwe functies in de vorige releases {#new-features-previous}

**1.4.30.**

* **Factureringscijfers**

Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek verzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.

**1.4.24.**

* **Blijvende netwerkverbinding**

Belangrijk: U moet ten minste Adobe Flash Player versie 22 of hoger hebben geïnstalleerd.
Met continue netwerkverbindingen wordt een interne lijst met netwerkverbindingen gemaakt en opgeslagen die opnieuw kan worden gebruikt voor meerdere aanvragen, in plaats van een nieuwe verbinding voor elke netwerkaanvraag te openen. Blijvende netwerkverbindingen moeten de efficiëntie verhogen en de latentie in uw netwerkcode verminderen.

In deze versie wordt deze functie niet ondersteund in Apple Safari en Mozilla Firefox op een Mac.

**1.4.19.**

* Ondersteuning voor streamintegriteit voor VPAID-advertenties.
* De optie voor het dempen van het tabblad in Flash Player FP 20.0.0.267 voor Firefox 42 en hoger is ingeschakeld door het hanteerprobleem op te lossen.

**1.4.18.**

* Primetime Desktop HLS TVSDK ondersteunt nu VPAID 2.0 Lineaire SWF-creatieven om een rijke interactieve in-stream ad-ervaring mogelijk te maken.

**1.4.10.**

* **Ad Fallback, Daisy chaining in ad selection logic (Zendesk #3103)** For VAST ads (creatives) with the fallback rule enabled, the TVSDK behandelt een advertentie met een ongeldig MIME type als een lege advertentie en probeert in plaats daarvan fallback-advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.

Zie [Extra fallback voor VAST- en VMAP-advertenties](../programming/tvsdk-1.4-for-android/ad-insertion/ad-fallback/android-1.4-ad-fallback.md) voor meer informatie.

**1.4.8.**

* **Video Heartbeats Library (VHL) bijgewerkt naar versie 1.5**

   * Mogelijkheid om metagegevens te verzenden met het starten van de video en/of het starten van de video/advertentie/hoofdstuk als contextgegevens
   * Minder netwerkverkeer - De hartslagen zijn gemiddeld minder en kleiner in grootte.

**1.4.7.**

* **Ondersteuning voor individuele support op locatie**

Steun voor op-gebouw installaties van de Server van de Individualisering van de Adobe om het de individualisatieverzoek van de cliënt aan te passen om naar een verschillend eindpunt te gaan.

**1.4.6.**

* **Voorbeeld-AES-codering (vereist Flash Player versie 17.0.0.134)**

AES-codering op basis van voorbeelden wordt nu ondersteund.

**1.4.2.**

* **Video Heartbeats Library (VHL)-update naar versie 1.4.0.1**

   * De mogelijkheid om verschillende analytische gebruiksscenario&#39;s te bundelen, van andere SDK&#39;s of spelers, met de Adobe Analytics Video Essentials.
   * Het bijhouden van advertenties is geoptimaliseerd door de methoden trackAdBreakStart en trackAdBreakComplete te verwijderen. Het ad-einde wordt afgeleid van de methodeaanroepen trackAdStart en trackAdComplete.
   * De eigenschap playhead is niet meer nodig bij het bijhouden van advertenties.

**1.4.0.**

* **Blackout Signaling With Alternate Content** ReplacementAls onderdeel van de 1.4 TVSDK-update ondersteunt de TVSDK nu ook het in- en terugkeren van regionale black-outs tegen lineaire inhoud. De TVSDK kan nu twee manifestbestanden parallel, hoofdbestand en alternatief verwerken om te controleren op uitstroomsignalen, zelfs wanneer alternatieve programmering wordt weergegeven in plaats van de oorspronkelijke programmering.

* **C3** Ads verwijderen/vervangenEr is nu geen extra voorbereidend werk nodig om nieuwe advertenties dynamisch in video-op-verzoek (VOD) activa op te nemen die uit het C3 venster komen. De TVSDK beschikt nu over een API waarmee u aangepaste inhoudsbereiken kunt verwijderen en dynamisch nieuwe advertenties kunt invoegen. Deze krachtige nieuwe functionaliteit is ook handig in gevallen waarin live/lineaire inhoud tijdens de uitzending wordt gerepareerd en onmiddellijk wordt afgetrokken voor gebruik als inhoud op aanvraag zonder dat er voldoende tijd is om het element &#39;schoon&#39; te maken.

## Opgeloste problemen {#resolved-issues}

>[!NOTE]
>
>Alle klanten van TVSDK die CRS gebruiken worden sterk aangemoedigd om aan minstens TVSDK 1.4.32 op iOS, Android, en Desktop HLS te bevorderen. Deze upgrade is een vervanging voor de bestaande app-implementatie. Na de upgrade controleert u de creatieve URL-aanvragen van CRS in een proxyprogramma (bijvoorbeeld Charles) om te controleren of de versie in het pad versie 3.1 weerspiegelt. Bijvoorbeeld:
>
>`https://adunit.cdn.auditude.com/assets/3p/v3.1/218747/94b/c1b/94bc1b964cc67e115a5a6781c7329b90_ee92607938ffff46b083121f044c2746.m3u8`

**Versie 1.4.41**

* Zendesk #33777 - Localhost token SWF voor DHLS distribution build expired.

   Het localhost-token bijwerken voor PMP-demo op DHLS.

### Opgeloste problemen in de vorige releases {#resolved-issues-previous}

**Versie 1.4.38** (891)

* Zendesk #30731 - TVSDK speelt geen veelvoudige VPAID advertenties in een AdBreak.

   Het afspelen van meerdere VPAID-advertenties in een AdBreak is opgelost.

* Zendesk #29968 - Double Billboard.

   De videospeler kan het laatste segment van een periode herhalen wanneer een schakelaar ABR gebeurt. Hierdoor werd het laatste segment van preroll soms herhaald. Dit is opgelost.

**Versie 1.4.35** (879)

* Zendesk #26058 - Ondersteunt native VPAID-gebeurtenissen

**Versie 1.4.33** (873)

* Zendesk #21701 - Verzend de oorspronkelijke creatieve URL voor het 1401 CRS-verzoek in plaats van de genormaliseerde URL.

   Het probleem waarbij al herverpakte URL&#39;s worden aangevraagd voor transcodering is opgelost, zoals vereist door de CRS-back-end.
* Zendesk #26197 - Anamorfe compressie wordt niet afgespeeld met de gewenste weergaveresolutie.

   **Opmerking**: Voor dit probleem is Flash Player 24.0.0.194 of hoger vereist.

   De kwestie waar de ontbrekende ingangen in de aspectverhouding lijsten werden gebruikt om de outputbreedte te berekenen is opgelost.

* Zendesk #26840 - HDCP-detectie mislukt op IE11 + Windows7 na tweede poging.

   **Opmerking**: Voor dit probleem is Flash Player 24.0.0.218 of hoger vereist.

   Dit probleem is opgelost door de verwerking van de hoofdwachtrij met berichten van AdobeCP te wijzigen om de hele wachtrij te doorlopen in plaats van alleen het eerste bericht te blokkeren.

* Zendesk #27460 - De nieuwe rekening Akamai kan geen POST CDN verzoek behandelen.

   Het nieuwe CDN-account kan een CDN-aanvraag van een POST niet verwerken. Dit probleem is opgelost door de code bij te werken zodat de cdn.auditude.com-aanvraag GET is in plaats van POST.
* Zendesk #27619 - Flash loopt vast op Windows 10

   **Opmerking**: Voor dit probleem is Flash Player 24.0.0.218 of hoger vereist.

   Dit probleem is opgelost door een fout als gevolg van lange URL&#39;s te voorkomen.

* Zendesk #28218 - Tracking event does not fire while the plackback from the resume point

   Dit is hetzelfde probleem als in Zendesk #26592. Het probleem waarbij zoekbewerkingen zijn toegestaan wanneer de mediaspeler de status PREPARED voor VOD-streams heeft, is opgelost.

**Versie 1.4.32** (867)

* Zendesk #26592 De gebeurtenis Tracking wordt niet gestart wanneer het afspelen begint vanaf het hervattingspunt

De code werkte het pre-rol en onderbrekingspunt niet bij wanneer het hervattingspunt niet nul was. Dit probleem is opgelost door logica toe te voegen om de code te vernieuwen wanneer de begintijd van het bereik niet overeenkomt.

* Zendesk #27022 Adds wordt niet gespeeld de tweede keer een activa wordt gespeeld

De uitzonderingen met de arraymethoden zijn hersteld.

**Versie 1.4.30** (855)

De volgende problemen zijn in deze release opgelost voor TVSDK:

* Zendesk #22898 - Ontbrekende ondertitels mogen het afspelen niet laten mislukken.

**Opmerking**: Voor dit probleem is Flash Player 23.0.0.185 of hoger vereist.

Dit probleem is opgelost door TVSDK toe te staan het afspelen voort te zetten, zelfs als het manifest de M3U8 van WebVTT mist, en gewoon een waarschuwing te registreren.

* Zendesk #23454 - Advertenties van derden (VPAID) worden niet correct verwerkt

Dit probleem is opgelost door VPAID-advertenties correct af te handelen op basis van inhoud-id&#39;s in plaats van tijdbereiken.

* Zendesk #24528 - Gebruikswaarden voor TVSDK voor facturering.

Belangrijk: Voor dit probleem is Flash Player 23.0.0.185 of hoger vereist.

* Zendesk # 25432 Closed Caption issue during resizing the player.

Belangrijk: Voor dit probleem is Flash Player 23.0.0.185 of hoger vereist.

De structuurcode van de weergave van het bijschrift is aangepast om de coördinaten tijdens het wijzigen van de grootte van de speler correct af te handelen.

De videokaart (VHL) is bijgewerkt naar versie 1.5.9 om de volgende problemen op te lossen:

* Zendesk #23730 - Metrische bitsnelheid is leeg

Dit probleem is opgelost door de wijzigingen in de bitsnelheid in VideoAnalyticsTracker bij te houden.

* Er is een nieuwe API, assetDuration, toegevoegd aan PTVVideoAnalyticsTrackingMetadata om de elementduur voor Live/Lineaire stromen bij te werken.

**Versie 1.4.28** (848)

* Zendesk #25027 - Auditude werkt niet in release 1.4.27

Dit probleem is opgelost door de code toe te voegen om AUDITUDE_METADATA_KEY te controleren en door AUDITUDE_METADATA_KEY en ADVERTISING_METADATA_KEY onderling verwisselbaar te maken.

* Zendesk #24428 - Frequent buffering issue using TVSDK to play a DRM HLS

Dit probleem is opgelost door er rekening mee te houden dat als er geen ad-setup is, TVSDK de verwerking kan versnellen door de wachtstand voor rollover en wachtstand en live reservering te verwijderen op de tijdlijn die is ontworpen om te synchroniseren en in te voegen.

* Zendesk #24344 - Schakel WebVTT-bestanden uit om de opstarttijden te verbeteren.

**Opmerking**: Voor dit probleem is Flash Player 23 of hoger vereist.

Dit probleem is opgelost door de WebVTT-bestanden alleen te laden als ondertitels moeten worden weergegeven.

* Zendesk #24994 - Ondertiteling met gesloten deuren wordt van de speler verwijderd wanneer het terugkeren van commerciële onderbreking

**Opmerking**: Voor dit probleem is Flash Player 23 of hoger vereist.

Door de onjuiste EOC-code verdween de weergave van het bijschrift. Dit probleem is opgelost door de codes 608 van de bijschriften RU2, RU3 en RU4 te dwingen de juiste zichtbaarheid in het huidige actieve venster te bieden.

**Versie 1.4.27** (844)

* Zendesk #21554 - TVSDK-foutbakens worden niet geactiveerd voor het toepassingstype = video/mp4

Dit probleem is opgelost door TVSDK de mogelijkheid te geven de juiste URL&#39;s voor het bijhouden van fouten op ongeldige elementindelingen te pingelen.

* Zendesk #23402 - Onvolledig en afspelen

**Opmerking**: Voor dit probleem is Flash Player 23 of hoger vereist.

Na het krijgen van een 404 fout op bepaalde verzoeken, zou een neerstorting kunnen voorkomen. Dit probleem is opgelost door ervoor te zorgen dat de verbinding niet wordt verbroken terwijl het antwoord wordt afgehandeld. De resolutie zorgt ervoor dat de VPAID-advertentiebestanden niet verkeerd worden geteld, zodat ze niet worden vrijgegeven tijdens het downloaden.

* Zendesk #23621 - Retry mislukt op 400 en 404

**Opmerking**: Voor dit probleem is Flash Player 23 of hoger vereist.

Probleem verholpen waarbij een DRM-metagegevensbeschadiging optrad bij het schakelen tussen verschillende profielen.

* Zendesk #23705 - Videoadvertenties bevriezen tijdens afbrekingen van AdStitched

**Opmerking**: Voor dit probleem is Flash Player 23 of hoger vereist.

Dit is hetzelfde probleem als in Zendesk #23621.

* Zendesk #23905 - Sommige pagina-einden worden overgeslagen op advertentiepunten

**Opmerking**: Voor dit probleem is Flash Player 23 of hoger vereist.

De inheemse voorzien van een netwerkcode van Vensters is bevestigd om ervoor te zorgen dat de verbindingen handvatten niet sluiten die momenteel door andere verbindingen worden gebruikt.

* Ticket #24029 - HLS FER stromen spelen niet alle middenroladvertenties in het middenrol.json dossier.

Dit probleem is opgelost door clients toe te staan aangepaste parameters afzonderlijk in te stellen voor de instantie Opportunity, zodat clients OpportunityGenerator niet hoeven te negeren.

**Versie 1.4.26** (839)

* Zendesk #18854 - Update creative selection logic based on CRS rules
   * Bied ondersteuning voor het bijwerken van creatieve selectielogica op basis van CRS-regels

* Zendesk #22725 - playbackManager.beginPlayback()-implementatie in de voorbeeldtoepassing voor Desktop

   * Correctie door deze overtollige vraag aan het eind van startPlaybackFromFlashVars te verwijderen aangezien de methode van setupVideo () wordt geroepen

* Zendesk #22807 - de verwijzingsuitzondering van SeekManager ongeldig

   * Probleem verholpen door de vereiste NULL pointer beveiliging in SeekManager te bieden met betrekking tot _dispatcher

* Zendesk #22822 - Frequent bufferen bij gebruik van TVSDK om een duidelijke HLS af te spelen

   * Opgelost door de eerste kans te verwijderen die door addSignalingModeOpportunityGenerator wordt gegenereerd als er geen advertentie is.

* Zendesk #23378 - Stream integriteitsblokken rules.xml

   * Probleem verholpen door het bestand rules.xml te laden via de workflow voor streamintegriteit.

**Versie 1.4.24** (817)

* Zendesk #19851 - Wanneer de speler zich aanpast aan een andere bitsnelheid, springt deze een paar frames terug in de tijd op de nieuwe bitsnelheid, waardoor een lastige ervaring ontstaat

**Opmerking**: Voor dit probleem is Flash Player 22.0.0.175 of hoger vereist.

Het probleem waarbij de DRM-adapter opnieuw wordt ingesteld nadat een klein deel van een segment is gedownload, wordt niet correct hersteld, is opgelost.

* Zendesk #20784 - Analytics: Het triggeren van inhoud wordt voltooid voor live video-overgangen

Dit probleem is opgelost door een API (trackVideoComplete) toe te voegen waarmee de inhoud handmatig kan worden voltooid tijdens een LINEAR/LIVE-videolesessie.

De volgende bibliotheken zijn bijgewerkt:

* Zendesk #21643 - VPAID-advertenties worden niet volledig afgespeeld

   * AdobeMobile-bibliotheek naar 4.10.0
   * VHL-bibliotheek naar 1.5.6
   * VHL-Nielsen-bibliotheek naar 1.6.7

Dit probleem is opgelost door een viewport met hoogte nul te gebruiken om het werkgebied te vullen wanneer een VPAID-advertentie wordt afgespeeld.

* Zendesk #22110 - Analytics: Voeg een veld h:sc:ssl toe aan aanroepen voor het bijhouden van de hartslag

De problemen met SSL zijn opgelost en de VHL-bibliotheek die wordt gebruikt in TVSDK, is bijgewerkt naar de nieuwste versie.

* Zendesk #22608 - Video toont periodiek een zwart scherm (vereist Flash Player 22.0.0.175 of later)

Tijdens adaptieve bitsnelheid, met de maximale bitsnelheidlimiet, wordt bij het opnieuw laden van de video periodiek een zwart scherm weergegeven, ook al ziet de client updates naar de positie, en de client gedraagt zich alsof de video inhoud afspeelt.

**Versie 1.4.23** (809)

* Zendesk #2887 - Post-roll en skipping kwestie wanneer de logica van de Regel van de Advertentie op TVSDK van toepassing was

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.240 of hoger vereist.

Het probleem waarbij de postroladvertenties werden overgeslagen toen de logica van de advertentieregel op de TVSDK werd toegepast, is opgelost.

* Zendesk #19863 - Toevoegen met VPAID-mediabestand verwijderd

Als een enorme inline-advertentie meerdere mediabestanden heeft met een VPAID-advertentie die de eerste advertentie is, wordt de inline-advertentie niet afgespeeld voor live streams. Dit probleem is opgelost door een ander mediabestand op te nemen.

* Zendesk #21021 - Late Binding Audio veroorzakende herhalingen van audiosegmenten

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.240 of hoger vereist.

Het probleem met het herhalen van audio is opgelost.

* Zendesk #21125 - Return from live/linear and break early

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.240 of hoger vereist.

Deze release biedt ondersteuning voor het retourneren van een advertentieeinde vroeg voordat het advertentieeinde wordt afgespeeld. De vroege terugkeer wordt vermeld door een markering van douanemanifest.

* Zendesk # 21369 Late binding audio veroorzaakt een inconsistente tijd

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.240 of hoger vereist.

Dit probleem is ook opgelost door het herhaalde audioprobleem dat is opgelost.

* Zendesk #21760, 20921 - Audio Video Desync op Seek.

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.240 of hoger vereist.

Het probleem met het herhalen van de audio is opgelost.

* Zendesk #22024 - Fout bij het uitvoeren van de TVSDK

Het probleem waarbij de referentiespeler geen stream afspeelt en bij het opstarten een uitzondering genereerde, is opgelost.

**Versie 1.4.22** (791)

* Zendesk #17580 - Runtimefout bij primetime met code 3357

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.197 of hoger vereist.

De willekeurige 3357 fouten die optraden door de deviceID correct te initialiseren wanneer storeVoucher() wordt aangeroepen, zijn opgelost.

* Zendesk #21334 - TVSDK en verzoek time-outwaarde voor advertenties van derden

In deze release is de time-out voor algemene advertenties toegevoegd.

**Versie 1.4.21** (782)

* Zendesk #19580 TVSDK wacht op voltooiing van de inhoudsoplosser voordat u `PTTimedMetadataChangedNotification`-berichten verzendt

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.182 of hoger vereist.

Dit probleem is opgelost in de Desktop Reference Player door de mogelijkheid te bieden om advertentietags in te stellen en een aangepaste opportuniteitsgenerator toe te voegen die aangeeft hoe u zich kunt abonneren op aangepaste cues en hoe u deze cues in een VOD-bestand kunt verwerken.

* Zendesk #20806 Future mid-roll advertenties in DVR window worden niet geactiveerd na het wisselen van cams

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.182 of hoger vereist.

Dit probleem is opgelost door de toepassing bij te werken naar de instelling _resource.metadata.setValue(DefaultMetadataKeys.ENABLE_LIVE_PREROLL, &quot;false&quot;) om de pre-roll en invoeging in een PIP-swap uit te schakelen en er wordt daarom geen pre-roll-mogelijkheid gegenereerd.

Er is een sorteerfunctie geïntroduceerd om de uit-van-volgorde en plaatsing te corrigeren die tot een negatieve duur van de hoofdinhoud hebben geleid.

* Zendesk #20522: Kan VPAID 2.0-advertenties niet overslaan

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.182 of hoger vereist.

* Dit probleem is opgelost door VPAID-advertenties over te slaan tijdens de advertentie.
* Wanneer het onderbrekingsbeleid wordt geplaatst om over te slaan, worden de gebeurtenissen van de advertentie en van de advertentie nog verzonden. De spelerstatus is inconsistent.

Dit probleem is opgelost omdat het zich correct gedraagt en geen gebeurtenissen verzendt wanneer een ad-break wordt overgeslagen.

* Zendesk #20955 Vastgestelde zeer belangrijke-waardeparen in het bezit customParameters door de opportuntiegenerator

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.182 of hoger vereist.

Het verzoek van de Audittegraad ontleedt AuditudeSettings voor douaneparameters wanneer het creëren van een advertentie-eenheid voor reclameverzoeken.

Dit gedrag is zodanig gewijzigd dat aangepaste parameters van het object Opportunity in de aanvraag worden opgenomen. Ook, kunnen de veelvoudige kansen met verschillende douaneparameters niet in één verzoek van de Auditude worden verpakt.

* Zendesk #21227 - m3u8 speelt niet consistent

**Opmerking**: Voor dit probleem is Flash Player 21.0.0.211 of hoger vereist.

Dit probleem is opgelost door de TVSDK toe te staan het manifest (HLS-subprofielen) te negeren dat de AC3-codec bevat die de TVSDK niet ondersteunt (surround).

**Versie 1.4.20** (762)

* Zendesk #19181 - Steen speelt snel vooruit naar live point loopt vast.

**Opmerking**: Voor dit probleem is Flash Player 20.0.0.306 of hoger vereist.

* Zendesk #19286 - Flash Player liep op tijdens het zoeken naar heen en weer in een FER stream.

**Opmerking**: Voor dit probleem is Flash Player 20.0.0.306 of hoger vereist.

De soms optredende hek bij het zoeken in Google Chrome werd opgelost door de query&#39;s af te sluiten, als het te lang duurt om een antwoord te krijgen of als de socket wordt afgesloten.

* Zendesk #19305 - Het afspelen van de hap vond plaats bij het afspelen van een stream met A/V-discontinuïteit.

**Opmerking**: Voor dit probleem is Flash Player 20.0.0.306 of hoger vereist.

Dit probleem is opgelost door een waarschuwing te melden.

* Zendesk # 19359 - Flash Player is vastgelopen vanwege de positie van #EXT-X-FAXS-CM: kenmerk in manifest op setniveau.

Dit probleem is opgelost wanneer de #EXT-X-FAXS-CM-tag boven aan de afspeellijst wordt weergegeven vóór afzonderlijke bitsnelheid of segmenten in de afspeellijst.

* Zendesk #19489 - Fast Forward to Live Point Stalls plugin (live stream)

Dit probleem is hetzelfde als Zendesk #19181.

* Zendesk #19699 - TVSDK schakelt niet tussen WebVTT-ondertiteltracks

Deze kwestie werd opgelost door de spelerstortplaats te maken en manifest opnieuw te laden wanneer een spoor verandert en door het UTF8 probleem van de koordomzetting te verbeteren dat de dubbel-byte WebVTT namen van titelsporen beïnvloedde.

**Versie 1.4.19** (1.4.19.738)

* Zendesk #18234 - Flash Player loopt vast bij het afspelen van streams met Unicode-tekenreeksen in CC

Dit probleem vereist Flash Player FP 20.0.0.267 of hoger en is opgelost door de Unicode-tekenreeks correct te verwerken.

* Zendesk #18304 - Ondersteuning voor stroomintegriteit voor VPAID-advertenties

Voor deze functie is Flash Player FP 20.0.0.267 of hoger vereist. Deze functie is geïntroduceerd in release 1.4.19.

* Zendesk #18766 - Reference Player kan geen niet-Latijnse Unicode-tekens weergeven in CC-tracknamen

Voor deze functie is Flash Player FP 20.0.0.267 of hoger vereist. De functie is hersteld door de Unicode-tekenreeks correct af te handelen.

* Zendesk #18804 - Speler loopt vast in Firefox 42

Voor dit probleem is Flash Player FP 20.0.0.235 of hoger vereist en hetzelfde probleem als Zendesk #18723.

* Zendesk #18864 - Flash Player volledige insteekmodule vastgelopen

Dit probleem vereist Flash Player FP 20.0.0.235 of hoger en is hetzelfde als Zendesk #18723.

* Zendesk #18998 - Als de audio- en videotijdstempels niet overeenkomen, is het eindeloos downloaden van segmenten bij discontinuïteit opgetreden.

Dit probleem is opgelost door de tussenruimte tussen tijdstempels te negeren en alleen de gedownloade inhoud af te spelen.

* Zendesk #19093 - Advertenties met middelste rol kunnen slechts eenmaal worden bekeken met live en full-event replay (FER) inhoud, maar deze advertenties konden niet opnieuw worden bekeken wanneer snel door:sturen of voorbij de advertenties zoeken

In de standaard adPolicy-kiezer van Primetime wordt de adBreak niet naar de gewenste positie verplaatst wanneer u een zoekopdracht uitvoert. Als u de advertentie na het zoeken opnieuw wilt afspelen, moet de toepassing de functie selectAdBreaksToPlay() overschrijven.

* Zendesk #19101 - Terugspoelen naar onopgeloste Midroll-advertenties verwijdert de advertentie.

Dit probleem is opgelost door de speler toe te staan de tijd playbackMetrics, minimumOpportunityTime en de Chronologie bij te werken.

* Zendesk #19102 - Problemen met de FER- en truc-modus

Voor dit probleem is Flash Player FP 20.0.0.267 of hoger vereist. Dit probleem is opgelost door het correct instellen van de advertentieMetadata.adSignalingMode.

* Zendesk #19175 - Soms worden pre-olladvertenties niet weergegeven wanneer de stream voor het eerst wordt afgespeeld.

Dit probleem is opgelost door een nieuwe API, adRequestTimeout, toe te voegen aan AuditudeSettings voor een time-out voor een advertentieverzoek. Gebruikers kunnen nu de standaardperiode van tien jaar overschrijven en een time-out aanvragen.

**Versie 1.4.18** (1.4.18.722)

* Zendesk #3324 - Rapportage voor primetime-advertenties houdt geen onderbrekingen bij wanneer er geen advertentiemedia in een VMAP aanwezig zijn.

Wanneer een advertentie-einde leeg is, werden de gebeurtenissen voor het starten en bijhouden van een advertentie niet gepingeld. Dit probleem is opgelost door het verzenden en afbreken van startpagina&#39;s op lege advertentieafbrekingen, zoals VMAP AdBreak, met een geldig AdSource-knooppunt.

**Versie 1.4.17** (1.4.17.702)

* Zendesk #17168 - Bijschriften worden na het schakelen van de zichtbaarheid gedurende 10 seconden niet weergegeven

Dit probleem is opgelost door ondersteuning te bieden voor de EXT-X-MEDIA-TIME-tag voor vtt-bijschriftbestanden.

* Zendesk #17983 - Het niet downloaden van om het even welke sleutels voor manifest veroorzaakt de volledige manifestplayback om te ontbreken

**Opmerking**: U moet minstens Flash Player FP 19.0.0.245 hebben of hoger.

Wanneer soms actieve inhoud wordt afgespeeld, kunnen er ongeldige sleutels in het manifest staan (bijvoorbeeld voor brainstormperioden), maar andere tijdbereiken hebben geldige sleutels en worden nog steeds afgespeeld. Eerder, toen een sleutel die in manifest werd vermeld niet kon worden gedownload, ontbrak volledig manifest. Nu, ontbreekt manifest slechts wanneer alle vermelde sleutels niet kunnen worden gedownload. Als sommige toetsen geldig zijn, maar sommige van deze toetsen niet kunnen worden gedownload, wordt de inhoud afgespeeld. We zullen nog steeds mislukken als we een segment proberen te spelen waarvoor een sleutel nodig is die we niet hebben.

* Zendesk #18554 - De Integriteit van de stroom die in sommige gevallen de koekjes in orde maakt

**Opmerking**: U moet minstens Flash Player FP 19.0.0.245 hebben of hoger.

Een fout in de code van de koekjesmanipulatie die koekjeswaarden kon beknotten werd opgelost.

**Versie 1.4.16** (1.4.16.684)

* Zendesk #3732 - Voeg ondersteuning toe voor proxy&#39;s in Chrome voor streamintegriteit (vereist Flash Player FP 19.0.0.207 of hoger)

Dit is een verbetering.

* Zendesk #4244 - Streaming problemen bij rollover PTS

Dit probleem is opgelost door rollover te detecteren en de discontinuïteit per ladingstype te beheren en niet algemeen.

* Zendesk #4487 - Lineair kanaal van inhoud volgen

Dit probleem is opgelost door videohartslagtracker opnieuw te initialiseren tijdens een lineaire streamafspeelsessie.

* Zendesk #17427 - Integriteit van de Adobe-stream die niet werkt via een proxy op Chrome (Win7) ()

**Opmerking**: De resolutie vereist Flash Player FP 19.0.0.207 of hoger.

Dit is hetzelfde als Zendesk #3732.

* Zendesk #17907 - Lag op pHLS Live Stream met Flash Player 19

**Opmerking**: De resolutie vereist Flash Player FP 19.0.0.207 of hoger.

Dit probleem is opgelost door de live streams te verwerken waarbij de domeinen van de TS-bestanden veranderen wanneer het live manifest opnieuw wordt geladen en de bestanden twee keer zijn gedownload.

* Zendesk #17931 - HLS-inhoud met leisteen aan het begin kan niet worden afgespeeld

**Opmerking**: De resolutie vereist Flash Player FP 19.0.0.207 of hoger.

Het probleem is opgelost door streams zonder audio af te handelen in de eerste 2 seconden van het eerste TS-bestand.

* Zendesk #17934 - Live streaming mislukt met Flash 19.0.0.185

**Opmerking**: De resolutie vereist Flash Player FP 19.0.0.207 of hoger.

Het probleem is opgelost door live streams af te handelen met tussenruimte tussen audio- en videoframes op segmentgrenzen.

* Zendesk #17973 - Nieuwste Flash Player 19.0.0.185 crashes tijdens de middelste rol

**Opmerking**: De resolutie vereist Flash Player FP 19.0.0.207 of hoger.

Het probleem is opgelost door ongedempte audio met middenrol en invoeging af te handelen. (De parserschakelaar komt voor, en op om het even welk punt in playback, overgaat de inhoud naar middenroladvertentie, of in het midden van advertentie, etc.)

* Zendesk #18049 - Flash 19 crasht met Firefox 42 beta

Dit is hetzelfde als Zendesk #17973.

**Versie 1.4.15** (1.4.15.678)

* Zendesk #4377: Fire AD_BREAK_SKIPPED-gebeurtenis bij het overslaan van een advertentie-einde vanwege het advertentiebeleid.

De correctie was om AD_BREAK_SKIPPED toe te voegen als een advertentie wordt overgeslagen.

* Zendesk #4496 - Stream Integrity: Fout 102100 met omleidingen naar gescheiden streams.

De oplossing bestond uit het toevoegen van ondersteuning voor het instellen van de AVNetworkConfiguration-eigenschap useCookieHeaderForAllRequests via de TVSDK.

* Zendesk #17179 - Flash speler crasht bij meerdere SAP-wijzigingen voor gecodeerde inhoud.

Een crash tijdens het afspelen van gecodeerde inhoud is opgelost.

**Opmerking**: Voor deze oplossing is Flash Player 19.0.0.200 of hoger vereist.

* Zendesk #17499 - Hoe kunnen we halffabrikaten na het horloge niet verwijderen, maar preroll uit de vetinhoud verwijderen?

Een type toegevoegd aan AdBreakTimelineItem (AdBreakTimelineItem.placementType) zodat AdPolicySelector een ander beleid voor pre-rol, middenrol, en post-rolinhoud kan terugkeren.

* Zendesk #17665 - Bandbreedte Throttling

De oplossing was het verwijderen van de logica om de buffergrootte van het doel in de aanvankelijke buffergrootte te veranderen wanneer het bufferen begint.

**Versie 1.14.14** (1.4.14.771)

* Zendesk #17363 - ReADME-documentatie voor de referentiespeler herstellen

   * Instructies voor het downloaden en installeren van playerglobal.swc verduidelijken.
   * Voeg instructies toe voor het bijwerken van projectconfiguratie met specifieke Flash Player-versie.
   * Werk AdvertisingOverlay project config bij om minimumspelerversie te gebruiken.
   * Update ReferenceCore project config om specifieke spelerversie 11.9 te gebruiken

* Zendesk #17471 - Player Freezes

Gedeeltelijke oplossing voor een probleem waarbij een advertentie niet vanaf het begin wordt afgespeeld na het zoeken.

* Zendesk #17496 - Podbuster wordt niet opgelost wanneer u terugzoekt in het DVR-venster

Geef aangepaste parameters op voor elk advertentieeinde.

**Versie 1.4.13** (1.4.13.660)

* Zendesk #4037 - Geen bruikbare profielfout (vereist Flash Player 18.0.0.232 of hoger)

probleem met url-parsering verhelpen wanneer queryparameter &quot;http&quot; bevat

* Zendesk #4260 - Flash Player 18 crashes in IE11 (vereist Flash Player 18.0.0.232 of hoger)

Probleem verholpen waarbij het afspelen van video in de modus Volledig scherm vastliep met IE11

* Zendesk #4262 - Adobe Primetime-speler loopt vast op Windows 10 (vereist Flash Player 18.0.0.232 of hoger)

Probleem verholpen waarbij het programma vastloopt wanneer video wordt afgespeeld in de modus Volledig scherm met FireFox in Windows.

* Zendesk #4279 - HLS TVSDK en invoeging -302 redirect issue on iOS and Desktop

Probleem verholpen waarbij het type van een URL niet correct werd herkend omdat deze geen extensie had

* Zendesk #4306 - Flash Player crasht wanneer alleen Windows op volledig scherm wordt uitgevoerd (vereist Flash Player 18.0.0.232 of hoger)

Oplossing voor een crash bij het afspelen van video in de modus Volledig scherm van Windows.

* Zendesk #4480 - Ontbrekende ID3-taggebeurtenissen (vereist Flash Player 18.0.0.232 of hoger)

**1.4.12 **(1.4.12.656)

* Zendesk #2751 - CSAI en CRS | Verbeteren: Dynamische elementen in bepaalde URL&#39;s van mediabestanden verwerken.

Bijgewerkte Creative Repackaging Service voor het correct verwerken van advertenties met dynamische creatieve URL&#39;s.

* PTPLAY - 2114 - ondersteuning voor MP4-afspelen.

Het afspelen van MP4-inhoud wordt nu ondersteund, inclusief afspelen, pauzeren en zoeken.

Voor het volgende is Flash Player 18.0.0.225 of hoger vereist:

* Zendesk #3992 - Aanvullende TrickPlay-snelheden.

TrickPlay accepteert nu snelheden hoger dan 16x: +/- 32, +/-64 en +/-128.

* Zendesk #3113 - Flash Player insteekmodule vastlopen

Probleem verholpen waarbij het programma vastloopt tijdens een poging om een advertentie om te leiden af te spelen op Mac Firefox.

* Zendesk #4037 - Geen fout in bruikbaar profiel
* Zendesk #4262 - Adobe Primetime Player crasht op windows 10

Correctie van vastlopen in Windows Firefox tijdens afspelen op volledig scherm.

**Versie 1.4.11** (1.4.11.648)

* Zendesk #1869 - Issue Changing Font Size (requires Flash Player 18.0.0.200)

Sta bijschriftgrootten toe om in WebVTT-bijschriftcode te worden gebruikt.

* Zendesk #3113 - Flash Player insteekmodule vastlopen (vereist Flash Player 18.0.0.200)
* Zendesk #3268 - Desktop: De videospeler begint na +- 40/50 seconden met flikkeren en begint na +- 90 seconden met zwart (vereist Flash Player 18.0.0.200)

Probleem met werkgebiedvideo verhelpen.

* Zendesk #3670 - fout INVALID_PARAMETER in VOD tijdens het zoeken in de Speler van de Verwijzing (vereist Flash Player 18.0.0.200)

InvalidateProfiles in ThreadSeek wanneer een nieuwe periode wordt ontdekt.

* Zendesk #3896 - Flash Player crasht met streamintegriteit ingesteld op ON op Chrome (vereist Flash Player 18.0.0.200)

Correctie van crash in native netwerkmodus van pepapparaat

* Zendesk #3905 - De TVSDK-speler wordt niet geladen wanneer deze wordt gehost op CDN

Het zoeken naar jokertekens voor jokertekens in gevallen waarin pageDomain anders is dan het SWF-domein, is nu opgelost.

**Versie 1.4.10** (1.4.10.642)

* Zendesk #3249 - TVSDK Web Player crashes Flash op Firefox

Probleem verholpen waarbij Firefox op de Mac soms vastliep terwijl een stream, die op een externe monitor wordt afgespeeld, overschakelde naar een hogere bitsnelheidsstream.(vereist Flash Player 18.0.0.160)

* Zendesk #3268 - Desktop: De videospeler begint na 40/50 seconden met flikkeren en begint na `+-` 90 seconden met zwart`+-`

Probleem verholpen met Mac Chrome waarbij de stream zou gaan flikkeren en uiteindelijk zwart zou worden. (vereist Flash Player 18.0.0.161)

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` macro wordt niet gevuld

   * foutcode 400 wordt weergegeven als deze inline is en slecht creatief is.
   * `[ERRORCODE]` macro wordt URL-gecodeerd

* Zendesk #3601 - Aanvraag tot verbetering: Beheer van de compacte onderneming

   * TVSDK geeft een wrappers-partner weer die bronnen (html, iframe of static) bevat die dicht bij de inline staan. (als de inline geen code voor die grootte bevat)
   * Wrappers gezelons met middel, tenzij gebruik voor vertoning, zal worden genegeerd. (niet gebruiken voor reeksspatiëring)
   * Alleen wrapper Companions met NO resource worden gebruikt voor traceringsdoeleinden. ( voor een verpakkingseenheid die alleen tekstspatiëring bevat )

**Versie 1.4.9**

* Zendesk #2615 - uitgave die de mening van HLS van Desktopvertoning verwijdert

ClearVideo()-methode toegevoegd aan MediaPlayer. Wist het weergegeven videoframe door de AVStream van het StageVideo-object te wissen. Moet alleen worden aangeroepen als de video is gepauzeerd en replaceCurrentResource of replaceCurrentItem moet worden aangeroepen voordat play() opnieuw kan worden aangeroepen.

* Zendesk #3169 - Update reference player met Adobe Analytics integration

Referentiespeler is bijgewerkt met Adobe Analytics-integratie

* Zendesk #3296 - Desktop HLS TVSDK - VAST, advertenties van derden die niet worden afgespeeld

Mime-typen voor HLS-indeling waren hoofdlettergevoelig, dit was onjuist en is gewijzigd, zodat ze niet langer hoofdlettergevoelig zijn

**Versie 1.4.8**

* Zendesk #2737 - Desktop Player - Fout 106000 (vereist Flash Player 17.0.0.184)
* Zendesk #3007 - Pre-roll advertenties die niet verschijnen na het bijwerken naar Flash Player 17 (vereist Flash Player 17.0.0.184)
* Zendesk #3085 - Desktop HLS Player verzendt fout 106000 na 60 seconden (vereist Flash Player 17.0.0.184)

**Versie 1.4.7**

* Zendesk #2760 - DISCONTINUITY-tag genegeerd tijdens TrickPlay-modus (vereist Flash Player versie 17.0.0.158)
* Zendesk #2760 - DISCONTINUITY-tag genegeerd tijdens TrickPlay-modus (vereist Flash Player versie 17.0.0.158)

**Versie 1.4.6**

* Zendesk #2652 - Auditude documentatie voor desktop HLS, Clarified Auditude media_id for desktop HLS documentatie

**Versie 1.4.5**

* Zendesk #2256 - Toegang tot Master afspeellijst, bijgewerkte PSDK om gebeurtenissen timedMetadata voor geabonneerde markeringen op master playlist te verzenden. (vereist Flash Player versie 17.0.0.134)
* Zendesk #2417 - Speler die ondertitels probeert te downloaden alvorens playbackbegin, WebVTT gebruikte de verkeerde variabele van het segmentaantal voor segmentaantalaanpassing. Er zou alleen een fout optreden voor media waarvoor de segmentindexen nul waren. (vereist Flash Player versie 17.0.0.134)
* Zendesk #2537 - Flash speler crasht wanneer de peperplug-in met Chrome wordt gebruikt (vereist Flash Player versie 17.0.0.134)
* Zendesk #2547 - Arabische ondertitels: Tekst moet rechts worden uitgelijnd (Flash Player versie 17.0.0.134 is vereist)

**Versie 1.4.4**

* Zendesk #1561 - Re: `[Adobe Primetime]` Bijwerken: HLS client based failover support for PROGRAM-DATE-TIME in Desktop PSDK (vereist Flash Player versie 16.0.0.305 of hoger)
* Zendesk #2197 - `[Ads]` Bijhouden en fouten
* Zendesk #2286 - Aanvraag van functies: Geef informatie op over de status voor het laden van advertenties (VPAID)
* Zendesk #2285 - Aanvraag van functies: Advertenties na een opgegeven tijdsduur overslaan
* Bug #3921755 - OpenSSL-bibliotheekupdate naar versie 1.0.1L in Flash Player (vereist Flash Player versie 16.0.0.305 of hoger)

**Versie 1.4.2**

* Zendesk #1303 - Verticale verschuiving voor Closed Caption (vereist Flash Player versie 16.0.0.235 of hoger, verwachte releasedatum: december 2014)
* Zendesk #1870 - Closed Caption On &amp; Off (vereist Flash Player versie 16.0.0.235 of hoger, verwachte releasedatum: december 2014)
* Zendesk #2110 - Afspelen blijft vastzitten nadat is geprobeerd het volledige scherm te betreden tijdens een VPAID-advertentie (vereist Flash Player versie 16.0.0.235 of hoger, verwachte releasedatum: december 2014)
* Zendesk #2199 - `[VPAID]` Player reageert niet tijdens het zoeken naar voorbij en onderbreking
* Zendesk #2358 - Re: `[Analytics]` Onjuiste hoofdstukgegevens

**Versie 1.4.1**

* De bijgewerkte Blackouts API is consistent met de Android- en iOS-implementatie.

**Versie 1.4.0**

* Zendesk #1024 - Functie voor het verwijderen van advertenties uit de stream via manifest
* Zendesk #1423 - De mislukking van de playback HLS vergrendelt omhoog Flash Player (zonder gemelde fout)
* Zendesk #1674 - ClosedCaption Niet zichtbaar, corrigeer de weergave van 708 bijschriften wanneer 0x03 ETX-codes ontbreken.

## Bekende problemen {#known-issues}

* Closed Caption werkt niet met alleen-audio inhoud omdat het bijschriftsysteem video nodig heeft om te werken.
Zonder video is er geen viewport-dimensie en zonder viewport-dimensie kunt u geen afbeeldingen voor bijschriften weergeven.
* De streamintegriteit in Google Chrome is iets trager vanwege beperkingen in de Chrome-sandbox.
* Als u autoPlay uitschakelt in TVSDK 1.4, kan een DRM-fout optreden wanneer de speler minstens een minuut inactief blijft. Om dit probleem te omzeilen, wanneer u autoPlay uitschakelt maar elementen vooraf laadt, wijzigt u `ReferenceCore.as` door de inhoud van `onPlaybackManagerPrepared` te wijzigen:

```
if (_playbackManager.autoPlay) {
_playbackManager.play();
} else {
_playbackManager.play();
_playbackManager.pause();
}
```

* **Versie 1.4.13** PTPLAY-8501 - wanneer VMAP twee directe MP4 niet-getranscodeerde advertenties terugkeert, de zelfde daling terug en speelt tweemaal.

* **Versie 1.4.2** In versie 16 van Flash Player werd een kwestie geïdentificeerd met ABR &quot;omschakelings neer&quot;logica, nadat de speler in een lege het bufferen gebeurtenis wordt. Het probleem voorkomt dat de bitsnelheid in slechte bandbreedteomgevingen omlaag gaat wanneer de speler in een bufferstatus komt. Om rond de kwestie te werken, laat uw app plaatsen `BufferControlParameters.initialBufferTime` om het zelfde als `BufferControlParameters.playbackBufferTime` tijdelijk tijdens de bufferstaat (namelijk op een `BufferEvent.BUFFERING_BEGIN` gebeurtenis) te zijn dan het terugstellen aan de vastgestelde waarden op `BufferEvent.BUFFERING_END` gebeurtenis. De oplossing voor dit probleem is beschikbaar in de volgende patchrelease van Flash Player versie 16.

* **Versie 1.4.0**

   * PTPLAY-1634 - de zelfde Geabonneerde markering heeft verschillende timestamps in verschillende levende vensters. Wanneer levende vensters zich bewegen, zou de zelfde markering in elk van hen zelfde timestamps moeten hebben. Soms hebben dezelfde tags echter verschillende tijdstempels.
   * PTPLAY-28 - De tijdlijn van MediaPlayer bevat geen lege einden.
   * Een bestand met interdomeinbeleid (crossdomain.xml) is vereist voor machtigingen om inhoud van een ander domein te streamen. [Een bestand crossdomain.xml instellen voor HTTP-streaming](https://www.adobe.com/devnet/adobe-media-server/articles/cross-domain-xml-for-streaming.html).
   * Bug #3694203 - In een DVR-stream kan het zoeken vanuit een rol halverwege de rol naar een andere medio-roll activering leiden tot blokkering van de browser
   * Bug #3753725 - selectPolicyForSeekIntoAd houdt geen rekening als het ad-einde is gecontroleerd
   * Bug #3754529 - Pre-roll advertenties worden niet verwijderd uit de stream wanneer ze terug zoeken in een live DVR-stream
   * Bug #3761896 - Als zoeken tijdens het afspelen van een advertentie is toegestaan, worden de advertentiemarkeringen na het zoeken opnieuw aangepast. De oplossing moet niet ITEM_UPDATED callback tijdens zoekactie gebruiken
   * Bug #3779889 - De volledige vraag wordt niet gemaakt wanneer het bereiken van het eind in truc spel in Video Analytics
   * Bug #VA-779 - De bitsnelheids verandering gebeurtenishartslag wordt niet verzonden voor Verbeterde Video Analytics met de Implementatie van de Verwijzing van de Verwijzing van de Steun van de Hartslag - het spel van de Steen wordt niet uitgevoerd in de steekproeftoepassing.

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).
