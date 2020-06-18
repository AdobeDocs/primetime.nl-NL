---
title: Opmerkingen bij de release TVSDK 1.4 voor Android
seo-title: Opmerkingen bij de release TVSDK 1.4 voor Android
description: In de Release-notities van TVSDK 1.4 voor Android wordt beschreven wat nieuw of gewijzigd is, welke problemen zijn opgelost en welke problemen bekend zijn en wat de apparaatproblemen zijn in TVSDK Android 1.4.
seo-description: In de Release-notities van TVSDK 1.4 voor Android wordt beschreven wat nieuw of gewijzigd is, welke problemen zijn opgelost en welke problemen bekend zijn en wat de apparaatproblemen zijn in TVSDK Android 1.4.
uuid: 8bd8ee42-7a1b-4c14-aad9-22804743e505
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: f1ebc1a8-185a-493a-9c00-a6102dffb128
translation-type: tm+mt
source-git-commit: 9c6a6f0b5ecff78796e37daf9d7bdb9fa686ee0c
workflow-type: tm+mt
source-wordcount: '7913'
ht-degree: 0%

---


# Opmerkingen bij de release TVSDK 1.4 voor Android {#tvsdk-for-android-release-notes}

In de Release-notities van TVSDK 1.4 voor Android wordt beschreven wat nieuw of gewijzigd is, welke problemen zijn opgelost en welke problemen bekend zijn en wat de apparaatproblemen zijn in TVSDK Android 1.4.

## Nieuwe functies {#new-features}

**Versie 1.4.43**

**Beveiligd laden van advertentie via HTTPS**

Adobe Primetime biedt een optie voor het aanvragen van een eerste aanroep naar primetime en server en CRS via HTTPS.

**alwaysUseAudioOutputLatency(boolean val) in MediaPlayer-klasse**

Wanneer deze parameter is ingesteld, gebruikt u de latentie van de audio-uitvoer in de tijdstempelberekening.

Er wordt een Booleaanse parameterwaarde geaccepteerd. Als de waarde `True`ervan is, gebruikt de client de latentie van de audio-uitvoer in de tijdstempelberekening.

**Versie 1.4.42**

**Gedeeltelijke invoeging van advertentie:**
TV-achtige ervaring om mee te doen in het midden van een advertentie zonder de tracking te starten voor de gedeeltelijk bekeken advertentie.
Voorbeeld: De gebruiker verbindt zich in het midden (bij 40 seconden) van een 90 seconde en onderbreking die uit drie 30 seconden bestaat. Dit is 10 seconden in de tweede advertentie in de pauze.
* De tweede advertentie wordt afgespeeld gedurende de resterende duur (20 sec.), gevolgd door de derde advertentie.
* Er worden geen trackers voor de gedeeltelijke advertentie geactiveerd (tweede advertentie). De trackers voor slechts de derde advertentie worden geactiveerd.

**Versie 1.4.41**

Geen nieuwe functies.

**Versie 1.4.40**

Geen nieuwe functies.

>[!NOTE]
>
>De API-wijzigingen zijn niet vereist als u een eerdere versie dan versie 1.4.39 gebruikt.

**Versie 1.4.39**

* TVSDK is gecertificeerd met VHL 2.0.1 en met VHL 2.0.1 met Nielsen.
* Android TVSDK wordt bijgewerkt en maakt CRS-aanvragen van de nieuwe Akamai-host `primetime-a.akamaihd.net`.
* De nieuwe hostnaamconfiguratie verstrekt activa CRS levering via zowel HTTP als HTTPS (SSL) op grotere schaal.
* TVSDK biedt ondersteuning voor de Android Oreo-release.
* Er wordt een nieuwe functie toegevoegd aan de `AdClientFactory` klasse ter ondersteuning van het registreren van meerdere Opportunity Detectors:

   ```
   public List<PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem item);
   ```

   Dit moet een array van PlacementOpportunityDetector retourneren. Nu kunt u meerdere Opportunity-detectors registreren. Bijvoorbeeld voor vroege en uitgangseigenschap, werden twee Detectors van de Kans vereist - voor toevoegings en een andere voor vroege uitgang uit advertentie. U moet deze nieuwe functie alleen implementeren als u uw eigen AdvertisingFactory hebt geïmplementeerd (en niet DefaultAdvertisingfactory gebruikt). Voor het ophalen van het bestaande gedrag moet u één Opportunity Detector maken, zoals in de functie createOpportunityDetector() en in een array en return:

   ```
   public class MyAdvertisingFactory extends AdvertisingFactory {  
   …  
   @Override  
   public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {  
   List&lt;PlacementOpportunityDetector&gt; opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector&gt;();  
   opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));  
   return opportunityDetectors;  
   } }
   ```

>[!NOTE]
>
>De API-wijzigingen zijn niet vereist als u een eerdere versie dan versie 1.4.39 gebruikt.

**Versie 1.4.36**

Opgeloste problemen voor inhoud overslaan op Android.

**Versie 1.4.35**

* **Netwerk en informatie**

   TVSDK API&#39;s bieden nu aanvullende informatie over VAST-reacties van derden. ID van de hulp, het Systeem van de Advertentie en de Uitbreidingen van VAST worden verstrekt in de klasse NetworkAdInfo die door het networkAdInfo bezit op een Middel van de Advertentie toegankelijk is. Deze informatie kan worden gebruikt voor integratie met andere Analytics-advertentieplatforms, zoals **Moat Analytics**.

**Versie 1.4.31**

**Ondersteuning voor meerdere CDN&#39;s voor CRS-advertenties**
* Standaard worden alle getranscodeerde elementen gehost op een CDN die eigendom is van Adobe op Akamai. Met de meest recente release biedt Adobe Creative Repackaging Service (CRS) u de mogelijkheid om de getranscodeerde creatieven te uploaden naar meerdere CDN&#39;s, zoals opgegeven door de klant.
* Nieuwe API&#39;s worden toegevoegd aan TVSDK om het opgeven van de uiteindelijke creatieve CRS-URL mogelijk te maken wanneer de standaard-URL niet wordt gebruikt. Raadpleeg de documentatie voor meer informatie over het gebruik van deze nieuwe API&#39;s.

**Versie 1.4.18** Primetime Android TVSDK biedt nu ondersteuning voor Javascript 2.0-creatieve VPAID&#39;s om een rijke interactieve functie en ervaring in de stream mogelijk te maken. Voor meer informatie over VPAID 2.0, zie [VPAID en steun](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/vpaid-ads/android-3x-vpaid-ads.md).

**Versie 1.4.17**

AC-3 5.1 wordt alleen ondersteund op Amazon FireTV.

**Versie 1.4.11**

* **Ad Fallback, Daisy chaining in ad selection logic (Zendesk #3103** for VAST ads (creatives) met de fallback-regel ingeschakeld, behandelt TVSDK een advertentie met een ongeldig MIME-type als een lege advertentie en probeert in plaats daarvan fallback-advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.

Zie [Extra fallback voor VAST- en VMAP-advertenties](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-fallback/android-3x-ad-fallback.md)voor meer informatie.

* **Video Heartbeats Library (VHL) bijgewerkt naar versie 1.5**
   * Mogelijkheid om metagegevens te verzenden met het starten van de video en/of het starten van de video/advertentie/hoofdstuk als contextgegevens
   * Minder netwerkverkeer - De hartslagen zijn gemiddeld minder en kleiner

**Versie 1.4.7**

* **Individualisatieondersteuning op locatie** voor on-premise installaties van de Adobe Individualization Server om het individuele verzoek van de client aan te passen en naar een ander eindpunt te gaan.

**Versie 1.4.6**

* **Voorbeeld-AES-codering (vereist Flash Player versie 17.0.0.134)**Voorbeeld-gebaseerde AES-codering wordt nu ondersteund.

**Versie 1.4.2**

* **Video Heartbeats Library (VHL)-update naar versie 1.4.0.1**

   * De mogelijkheid om verschillende analysemogelijkheden te bundelen, van andere SDK&#39;s of spelers, met de Adobe Analytics Video Essentials.
   * Het bijhouden van advertenties is geoptimaliseerd door de methoden trackAdBreakStart en trackAdBreakComplete te verwijderen. Het ad-einde wordt afgeleid van de methodeaanroepen trackAdStart en trackAdComplete.
   * De eigenschap playhead is niet meer nodig bij het bijhouden van advertenties.

* **Nielsen SDK** IntegrationTVSDK ondersteunt nu het verzenden van informatie voor het bijhouden van gebruikers naar de Nielsen SDK zonder aangepaste integratie.

**Versie 1.4.0**

* **Blackout Signaling with Alternate Content Replacement** Als onderdeel van de 1.4 TVSDK-update ondersteunt de TVSDK nu ook het in- en terugkeren van regionale black-outs tegen lineaire inhoud. De TVSDK kan nu twee manifestbestanden parallel, hoofdbestand en alternatief verwerken om te controleren op uitstroomsignalen, zelfs wanneer alternatieve programmering wordt weergegeven in plaats van de oorspronkelijke programmering.

* **C3-advertenties** nu verwijderen/vervangen; er is geen extra voorbereidend werk nodig om nieuwe advertenties dynamisch in video-op-verzoek (VOD)-elementen in te voegen die uit het C3-venster komen. De TVSDK beschikt nu over een API waarmee u aangepaste inhoudsbereiken kunt verwijderen en dynamisch nieuwe advertenties kunt invoegen. Deze krachtige nieuwe functionaliteit is ook handig in gevallen waarin live/lineaire inhoud tijdens de uitzending wordt gerepareerd en onmiddellijk wordt afgetrokken voor gebruik als inhoud op aanvraag zonder dat er voldoende tijd is om het element &#39;schoon&#39; te maken.

* De interface PlaybackEventListener heeft een nieuwe methode genoemd onReplaceMediaPlayerItem, die u kunt gebruiken om naar een nieuwe gebeurtenis te luisteren, `ITEM_REPLACED`. Deze gebeurtenis wordt verzonden wanneer een instantie MediaPlayeritem op MediaPlayer wordt vervangen. De clienttoepassing die deze PlaybackEventListener implementeert, moet deze nieuwe methode implementeren of overschrijven.
* AdClientFactory heeft een nieuwe functie toegevoegd aan de klasse om te registreren voor meerdere Opportunity-detectors:

   public List&lt;PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem-item);

   Bijvoorbeeld voor vroege en uitgangseigenschap, hebt u twee Detectors van de Kans nodig - voor toevoegings en een andere voor vroege uitgang van `ad`.

   Als u deze nieuwe functie wilt overschrijven, maakt u één opportuniteitsdetector die in een array en return wordt geplaatst:

   @Override

   public List&lt;PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {

   List&lt;PlacementOpportunityDetector> opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector>();

   opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));

   return opportunityDetectors;
}

   }

## Wijzigingen voor TVSDK voor 1.4 {#tvsdk-changes}

* De interface PlaybackEventListener heeft een nieuwe methode genoemd onReplaceMediaPlayerItem, die u kunt gebruiken om naar een nieuwe gebeurtenis te luisteren, ITEM_REPLACED. Deze gebeurtenis wordt verzonden wanneer een instantie MediaPlayeritem op MediaPlayer wordt vervangen. De clienttoepassing die deze PlaybackEventListener implementeert, moet deze nieuwe methode implementeren of overschrijven.

* AdClientFactory heeft een nieuwe functie toegevoegd aan de klasse om te registreren voor meerdere Opportunity-detectors:

public List`<PlacementOpportunityDetector>` createOpportunityDetectors (MediaPlayerItem-item);

Voor bijvoorbeeld de functie voor vroege advertenties en het afsluiten hebt u twee Opportunity-detectors nodig: een voor invoeging in advertentie en een andere voor het vroegtijdig afsluiten van een advertentie.

Als u deze nieuwe functie wilt overschrijven, maakt u één opportuniteitsdetector die in een array en return wordt geplaatst:

@Override

public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {

List`<PlacementOpportunityDetector>` opportunityDetectors = new ArrayList`<PlacementOpportunityDetector>`();

opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));

return opportunityDetectors;

}

}

## Apparaatcertificering en ondersteuning in 1.4 {#device-certification-and-support-in}

>[!NOTE]
>
>De volgende functies worden **niet** ondersteund in de TVSDK:
>
>* Trage beweging op elk platform of elke versie.
>* Live truc.


**Versie 1.4.43**

TVSDK 1.4.43 is gecertificeerd met Android-apparaten met Android 6.0.1/ 7.0 en 8.1 (Oreo).

* **Versie 1.4.23:**

   * TVSDK 1.4.23 is gecertificeerd voor Android-apparaten met Android N.

* **Versie 1.4.18:**

   * Primetime is gecertificeerd voor Amazon Fire TV.
   * VPAID 2.0 wordt alleen ondersteund op apparaten met Android 4.0 en hoger.

## Opgeloste problemen in 1.4 {#resolved-issues-in}

>[!NOTE]
>
>Alle TVSDK-klanten die CRS gebruiken, worden sterk aangeraden om te upgraden naar TVSDK 1.4.39 of hoger op iOS en Android. Deze upgrade is een drop-in vervanging van de bestaande app-implementatie. Na de upgrade controleert u de creatieve URL-aanvragen van CRS in een proxyprogramma (bijvoorbeeld Charles) om te controleren of de versie in het pad versie 3.1 weerspiegelt. Bijvoorbeeld:
>
>`https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8`

**Versie 1.4.43**

* Ticket #27143 - Kan de 5.1-audiotrack niet afspelen op FireTV-apparaten

   * TVSDK kan nu AC3-audio afspelen op FireTV-apparaten. Afspelen vindt altijd plaats in stereo.

* Ticket #33902 - Beveiligde levering van advertenties via HTTPS

   * Adobe Primetime biedt een optie waarmee u een eerste oproep naar primetime en server en CRS via https kunt uitvoeren.

* Ticket #34493 - Bluetooth-audiovertraging

   * Toegevoegd `alwaysUseAudioOutputLatency` in de MediaPlayer-klasse. Wanneer deze is ingesteld, wordt de latentie in de audio-uitvoer gebruikt bij de tijdstempelberekening.

* Ticket #34949 - Nieuwe versie van geïntegreerde videohartslagbibliotheek (VHL).

**Versie 1.4.42 (1791)**

* Zendesk #33719: De Adaptieve bitsnelheid van FireTV 4k wordt langzaam geschaald. Extra ondersteuning voor ABR voor FireTV 4K-apparaten.
* Zendesk #33338:  resetDRM wist alle gegevens van de toepassing.  Behandelde extra geval waar de uitzonderingen in verbindingen niet - TVSDK de verrichtingsrijen van TVSDK omhoog veroorzaakten.

**Versie 1.4.41 (1776)**

* Zendesk #33002 - Companion asset data van TVSDK op Fire TV. Geïmplementeerd een nieuwe klasse AdBannerAsset die de Companion-gegevens retourneert als List &lt;AdBannerAsset> en AdAsset::id is nu een tekenreeks in plaats van lang.
* Zendesk #32821 - Android Primetime speler bevriest wanneer het de Tijdstempel van de Presentatie (PTS) voor WWE ontmoet. Dit probleem is opgelost in deze release.
* Zendesk #33572 - VideoAnalyticsProvider en Start vastlopen. Met de juiste combinatie van VHL+Nielsen joint SDK-versie van VideoHeartbone.jar heeft u dit probleem opgelost.
* Zendesk #33355 - Fire TV: 15 seconden terug. Geen enkele oplossing van TVSDK en de klant verifieert dit aan het eind en van derden.

**Versie 1.4.40 (1764)**

* Zendesk #33068 - Amazon lip sync issue on new device. Het synchronisatieprobleem met de app is opgelost in deze releases.
* Zendesk #32215 - Android TVSDK 1.4.38 Beveiligingsproblemen `[Hotlist]`. Bijgewerkt naar de nieuwste OpenSSL-1.1.0 en curl-7.5.1.
* Zendesk #32920 - Leeg scherm binnen een Ad-einde en geen Ad-break-voltooiing. Probleem verholpen waarbij een VPAID-container een blokkeringsstatus kon krijgen en een probleem behandelde waarbij VPAID-advertenties van Facebook vaak meerdere CDATA-blokken in één \&amp;amp retourneren;lt;AdParameters\&amp;gt; VAST-knooppunt.

**Versie 1.4.39 (1744)**

* Zendesk #28976 - Vergunningsaanvraag duurt meer dan een seconde. Terwijl de DRM vraag van het vergunningsverzoek die POST gebruikt uitvoert, voegt Krol extra &quot;Verwacht toe: 100-continue&quot; header. Verwijderd Koptekst &quot;Verwacht:&quot; in TVSDK.
* Zendesk #27707 - CSAI milieu&#39;s respecteren geen KUINE IN tellers voor vroege terugkeer of terugkeer naar inhoud. Bied ondersteuning voor meerdere opportuniteitsproducenten.

**Versie 1.4.38 (1722)**

* Zendesk #21590 - Video Performance and Tracking in Latest Origin Builds

Integratie en certificering van VHL 2.0 in TVSDK om de barrière in de implementatie VideoHeartbeatsLibrary te verminderen door de complexiteit van de API&#39;s te verminderen.

* Zendesk #29688 - Ondersteuning voor klanten van Android O Beta.

TVSDK-ondersteuning voor de nieuwe Android-bètaversie.

**Versie 1.4.36 (1713)**

* Zendesk #27392 - Inhoud overslaan op Android

Om decodering mogelijk te maken, breidde de Android TVSDK het bytebereik van niet-iframe-inhoud ten onrechte met 16 bytes uit. De verbreding is nodig voor Iframe-streams, maar niet voor niet-iframe-streams.

**Versie 1.4.34 (1702)**

* Zendesk #27638 - Leak in cURL INet-object

Het Posix cURL INet-object lekt tijdens het vasthouden aan de ShareManager en de DNS-cache die in de cURL-verbindingen werd gebruikt.

Dit probleem is opgelost door het Inet-object Posix cURL te verwijderen uit de Inet-deconstructor.

**Versie 1.4.33 (1694)**

* **OpenSSL-bibliotheek**

De OpenSSL-bibliotheek is bijgewerkt met OpenSSL versie 1.0.2j.

* Zendesk #21701 - Verzend de oorspronkelijke creatieve URL voor het 1401 CRS-verzoek in plaats van de genormaliseerde URL.
Dit probleem wordt opgelost door de oorspronkelijke creatieve URL&#39;s te verzenden.

* Zendesk #25023 - Video&#39;s met lange duur afspelen: video bevriezen, schermflikkeringenDit probleem is opgelost door de maximale videoformaten voor CenturyLink-set-top box-apparaten in te stellen.

* Zendesk #27460 - De nieuwe rekening Akamai kan een POST cdn- verzoek niet behandelen.
De code is bijgewerkt om het `cdn.auditude.com` advertentieverzoek om GET in plaats van POST te maken.

* Zendesk #28245 - De staat van de Playback wordt niet correct gemeld wanneer app van achtergrond naar voorgrond gaat. Dit probleem werd opgelost door de playbackstaat correct te herstellen om te spelen of te pauzeren wanneer de toepassing op de voorgrond terugkeert.

**Versie 1.4.32 (1682)**

* Zendesk #25779 - Beveiligingskwetsbaarheid gevonden met TVSDKAndroid 4.2 en lager heeft een beveiligingskwetsbaarheid wanneer JavaScript is ingeschakeld in een WebView. Het gebruik van WebView door TVSDK is uitgeschakeld voor apparaten met OS 4.2 of lager. Hierdoor wordt het gebruik van VPAID-advertenties in TVSDK op deze apparaten uitgeschakeld.

* Zendesk #26890 - Issue in SCREEN state (ON/OFF) handling Ref. PlayerWanneer de Adobe Video Engine (AVE) wordt hervat vanuit een GESUSPENDEERDE status, werkt DefaultMediaPlayer de status niet bij. Dientengevolge, blijft DefaultMediaPlayer in een GESUSPENDED staat alhoewel AVE in een SPELENDE staat is. Dit probleem is opgelost door de status DefaultMediaPlayer in te stellen op AFSPELEN bij het ontvangen van een afspeelstatus van de AVE, zelfs als de huidige status van DefaultMediaPlayer WORDT GESUSPENDEERD.

**Versie 1.4.31 (1675)**

* Zendesk #21974 - Uitzonderingen vanwege null-objecten
   * AdIndex wordt zelden verhoogd wanneer deze null is. Dit kan te wijten zijn aan onjuiste API-aanroepen die zijn ontvangen voor pre-roll adBreak. De gegevenstypen zijn gecorrigeerd om dergelijke uitzonderingen te voorkomen.

* Zendesk #24714 - Externe logboekregistratie uitschakelen
   * Bijgewerkt TVSDK om het externe registreren uit te zetten

* Zendesk #24488 - AV-synchronisatieproblemen op Fire TV
   * Probleem verholpen door de afhandeling van de AV-decoderthreads te verbeteren. Wanneer de invoer- of uitvoerframewachtrijen worden gewijzigd, wordt met name de decoderingsverbinding uitgevoerd die specifiek is voor het inhoudstype van het frame.

* Zendesk #26551 - De CRS-fouten verhelpen
   * Wanneer het verzoek HEAD (http head) is, hoeven we de inhoud niet te lezen omdat deze leeg is. Hoewel het ok is om te proberen het te lezen, loopt oude Android (4.0.x) vast terwijl we read() aanroepen en de nieuwere Android retourneert de juiste waarde (-1) wanneer we read() aanroepen. Op basis hiervan is de code gewijzigd en is de inhoud voor &quot;head&quot; niet gelezen

* Uitzondering voor Null-aanwijzer in Zendesk #26696 bij toegang tot TrickPlayManager
   * Probleem verholpen door te controleren of het TrickPlayManager-object niet null is voordat het wordt gebruikt.

**Versie 1.4.30 (1659)**

* De tijdsduur van het element Zendesk #22675 wordt niet bijgewerkt voor Live/Lineaire streams. Dit probleem is opgelost door een nieuwe API, assetDuration, op te geven in PTVideoAnalyticsTrackingMetadata die de elementduur voor live en lineaire streams biedt.

* Zendesk #25853 Geheugenlek in TVSDK wanneer het schakelen van kanalenHet probleem waar een dossier-gelezen bufferlek wanneer MediaPlayer wordt teruggesteld of vrijgegeven terwijl het downloaden van een dossier is opgelost.

**Versie 1.4.29 (1653)**

* Zendesk #21200 - Player herstelt zich niet van de stilstaande toestand wanneer de toepassing op de achtergrond werd uitgevoerd. Wanneer de speler werd onderbroken nadat de streamschakelaar was gesignaleerd, kan de speler met de resolutie de streamschakelaar uitvoeren wanneer de speler wordt teruggezet vanaf de status &#39;suspend&#39; in plaats van de vorige positie te herstellen.

* Zendesk #23412 - Speler zit vast met een zwarte doos als u door om het even welke Advertenties binnen de laatste 3s van de advertentierak klikt. Dit probleem is de zelfde kwestie zoals Zendesk #21200.

* Zendesk #23616 - Overgeslagen ad break zoekt te ver in de toekomst. Afhankelijk van het invoegtype (invoegen/vervangen) bepaalt TVSDK of de ad-duur wordt gebruikt in de berekening om het eindpunt van de advertentie te bepalen.

* Zendesk #25078 - TVSDK DRM Geheugenlek op Android TV STBTHet geheugenlek voor het DRM-adapterobject is gevonden en hersteld.

* Zendesk #25067 - Crash in VideoEngineTimelineDit gebeurt omdat de objecten niet correct zijn schoongemaakt en gebeurtenissen werden aangeroepen nadat de objecten waren vernietigd. Het probleem is opgelost door controles toe te voegen om null-uitzonderingen te voorkomen.

* Zendesk #25352 - Vastgestelde de kopbal van douaneDeze kwestie werd opgelost door een nieuwe douanekopbal aan toe te voegen sta lijst op TVSDK toe.

* Zendesk #25617 - de Levende rollover van stroom PTS die spelerdiscontinuïteit en geheugencrash veroorzaakte. Dit probleem is opgelost door een PTS rollover-verwerking toe te voegen in FragmentedHTTPStreamer wanneer een rollover plaatsvindt in het midden van een segment.

**Versie 1.4.28 (1637)**

* Zendesk #23618 - Gebeurtenissen voor regeleinden branden voordat het advertentiebeleid wordt geraadpleegdDit probleem is opgelost door de gebeurtenissen AD_BREAK_START en AD_START niet te negeren wanneer de advertentie wordt overgeslagen vanwege de advertentie. De gebeurtenis AD_BREAK_SKIPPED wordt in plaats daarvan verzonden.

**Versie 1.4.27 (1631)**

* Zendesk #23174 - Prestatieprobleem bij het wijzigen van de grootte van de video. Dit probleem is opgelost door een nieuwe API aan te tonen, MediaPlayerView.setSurfaceFixedSize, waarmee TVSDK toegang heeft tot SurfaceHolder.setFixedSize() vanuit MediaPlayerView.

* Zendesk #24450 - TVSDK doet dubbele advertentieverzoekenDit probleem is opgetreden toen de verstreken tijd werd omgezet in lang en niet dubbel, en dit probleem is opgelost.

**Versie 1.4.26 (1627)**

* Zendesk #21436 - OpenSSL-bibliotheekupdate naar versie 1.0.2h De OpenSSL-bibliotheek is bijgewerkt naar OpenSSL versie 1.0.2h
* Zendesk #23825 - Cookies worden niet opgenomen in de callbacks Fixed door de ondersteuning voor android cookies te bieden.

**Versie 1.4.25 (1620)**

* Zendesk #22900 - Live Adobe Primetime DRM-stream wordt niet afgespeeld op de Android-referentiespeler. Het probleem met de geheugentoewijzing is opgelost.
* Zendesk #23176 - De toepassing loopt vast wanneer deze VPAID-advertenties probeert af te spelen. Het programma is vastgelopen omdat de toepassing geen aangepaste advertentieweergave maakt om een VPAID-advertentie te renderen. Dit probleem is opgelost door de VPAID-advertenties in de reactie van de advertentieserver te negeren als er geen aangepaste advertentieweergave is.

* Zendesk #23153 - SampleAES DRM Stream - Playback stalling in de TVSDK Reference PlayerDit probleem is hetzelfde als Zendesk #22900.

**Versie 1.4.24 (1612)**

* Zendesk #20784 - Analytics: Het uitproberen van inhoud wordt voltooid voor live video-overgangen. Dit probleem is opgelost door een API (trackVideoComplete) toe te voegen die handmatig het voltooien van de inhoud tijdens een live/lineaire videolesessie activeert.

* Zendesk #21977 VideoEngineTimeline crash during placeAdBreak/acceptAd operation
   * In deze uitgave zijn de volgende bibliotheken bijgewerkt:
      * AdobeMobile-bibliotheek naar versie 4.10.0
      * VHL-bibliotheek naar versie 1.5.6
      * VHL-Nielsen-bibliotheek naar versie 1.6.7

Dit probleem is opgelost door een null-controle toe te voegen voordat advertenties werden toegevoegd aan de geaccepteerde advertentielijst.

* Zendesk #22313 De bitsnelheid voor STBs met Amilogic chipset gaat niet verder dan 1,2MTDit probleem is opgelost door de mogelijkheden van de media-codec vooraf te laden en de naadloze switch voor Amilogic chipset-apparaten uit te schakelen.

* Zendesk #19520 Sample AES HLS-element wordt niet afgespeeld in TVSDK-spelers. Dit probleem is opgelost door het verwerken van meerdere PMT-descriptors voor met AES gecodeerde HLS-streams met Sample.

**Versie 1.4.23 (1602)**

* Zendesk #18852 - Update creative selection logic based on CRS rulesThis issue was resolved by adding a JSON configuration file to specify the creative selection priority.

* Zendesk #20861 - Android NTThis release biedt ondersteuning voor Android N door de mogelijkheid te verwijderen om de native bibliotheken van het Android-platform rechtstreeks te gebruiken die niet meer toegankelijk zijn voor toepassingen die op Android N worden uitgevoerd.

* Zendesk #21018 - Android N crashDezelfde resolutie als ZD# 20861.

* Zendesk #21266 - VideoEngineAdapter loopt vast op een Invalid_Key foutDe Invalid_Key fout bevat geen beschrijving van AVE, zodat resulteerde het ontleden van de tekst in NPE. Het probleem is opgelost door een null-controle voor de beschrijving tijdens onError toe te voegen voordat de beschrijving werd geparseerd.

* Zendesk #22286 - de inheemse bibliotheek gaat op het toewijzen van geheugenlezende sleutel/het fragment veroorzaken crashDeze botsing die op Android voorkwam wanneer het proberen om manifest met veelvoudige sleutels gelijktijdig te laden is opgelost.

**Versie 1.4.22 (1581)**

* Zendesk #17236 - Onbetrouwbare playhead time voor video&#39;s HLS met DRMTthe time jump with the LBA streams, where the audio segment start time does not match with the video segment start time, has fixed.

* Zendesk #17680 - Video playback bevriest op de Selevision Andredo doosDe videodecoder op dit apparaat keert soms een significante outputtijdsprong terug wanneer het deijden van videoframe van de outputbuffer, en dit outputtimestamp blijft hoog. Dit probleem is opgelost door een *videoprofiel te retourneren dat niet wordt ondersteund* . Hierdoor wordt de speler niet gedwongen hetzelfde profiel opnieuw te proberen of een ander profiel te kiezen.

* Zendesk #19074 - Video bevriest tijdens FWD en REW-truc-playDit probleem is opgelost door een nieuwe waarschuwing toe te voegen aan TRICKPLAY_ENDED_DUE_TO_ERROR om aan te geven dat trickplay is afgesloten en dat de video is gepauzeerd vanwege een onherstelbare fout.

* Zendesk #19574 - TVSDK retourneert geen M3U8-responsgegevens voor DRM- of niet-DRM-inhoud. Dit probleem is als volgt opgelost:

* Zendesk #19986 - OP-gedrag mislukt voor bepaalde apparaten zoals Android TV
* Een FILE_NOT_FOUND-fout toevoegen aan de voorwaarde.
* Wanneer de fout afkomstig is van een *bestand dat niet is gevonden* , scheidt u de URL en het antwoord van de foutbeschrijving als het antwoord beschikbaar is.
De logische fout die is geïntroduceerd door de IP-ondersteuning van het NVidia-schild is opgelost. Vertrouw op niet-NVidia-schermapparaten op de veilige markeringen voor de weergave, zelfs als het weergavetype onbekend is.

* Zendesk #20549 - Handling of stale playlists. Deze kwestie werd opgelost door het interval tussen de levende duidelijke update tot de helft van de verwachte segmentduur te verminderen, als vorige halen geen nieuwe segmenten ontvangt.

* Zendesk #20742 - Het geheugengebruik lijkt te blijven stijgen wanneer het spelen van levende inhoud op FireTV.De botsing wordt veroorzaakt door de JNI objecten verwijzingstabel die de grens heeft bereikt. Dit probleem is opgelost door de verwijzing naar het MediaFormat-object te verwijderen dat is gemaakt tijdens het opnieuw opstarten van de decoder.

* Zendesk #21125 - Return from live/linear ad break early (CSAI). Er is een functie toegevoegd waarmee de speler tijdens een advertentie-einde kan terugkeren naar de hoofdinhoud als de speler de splice in ad-cues registreert met de splice in opportunity-detector.

* Zendesk #21334 - TVSDK en request timeout value for third-party ad request. Er is een adRequestTimeout-instelling toegevoegd aan AdvertisingMetadata die een algemene time-out voor de advertentieaanroep mogelijk maakt.

**Versie 1.4.21 (1566)**

* Zendesk #17781 - ADB screencapture werkt niet meer. Dit probleem is opgelost door de API DefaultMediaPlayer.create (Context, Boolean secureSurface) toe te voegen, die schermvastlegging toestaat.
Als u schermvastleggingen wilt toestaan, geeft u false door voor secureSurface.
Belangrijk: We raden u ten zeerste aan deze functie voor het vastleggen van schermen niet in te schakelen bij een productie-instelling.

* Zendesk #19074 - Video bevriest tijdens FWD en REW-trucDe volgende problemen die optraden toen de trucPlay in de afspeelfilm kon bevriezen, zijn opgelost:

* Zendesk #19532 - Bijschrift sluiten komt buiten orde
   * FHS start trickplay, maar het eerste iframe segment had er geen frame in.
   * Wanneer tijdens het downloaden van een iframe-segment FHS een fout optreedt, wordt het segment afgesloten bij het afspelen en wordt het afspelen gepauzeerd.
   * De Android MediaCodec-implementatie wacht altijd op beschikbaarheid van de invoerwachtrij terwijl werd gevraagd om alle invoer-/uitbuffers te verwijderen.
Dit probleem is opgelost door de volgorde van WebVTT-cues om te keren, zodat meerdere overlappende cues &#39;omhoog&#39; lijken te schuiven.

* Zendesk #19574 - De TVSDK retourneert geen M3U8-responsgegevens voor DRM- of niet-DRM-inhoudBij de eerste belasting van het manifestbestand in PTMediaPlayerItem.prepareToPlay rapporteert de TVSDK, als het laden mislukt, niet de hoofdtekst van de mislukkingsreactie op de toepassing.
Dit probleem is opgelost door de TVSDK toe te staan de mislukkingsreactie als een fout aan de toepassing te melden.

* Zendesk #19701 - Het afspelen bevriest met SAP/DiscontinueDe speler bevriest wanneer de audio en video niet zijn uitgelijnd bij discontinuïteit is opgelost.

* Bug #PTPLAY-11162 - De update van de OpenSSL-bibliotheek naar versie 1.0.2f is opgelost.

**Versie 1.4.20 (1546)**

* Zendesk #17384 - Aanvraag van functies: ID3-metagegevensondersteuning voor AAC-afspelenOndersteuning voor ID3-tags in AAC-media is geleverd in de TVSDK voor Android vanaf versie 1.4.20.

* Zendesk #18358 - Speler bevriest op bitsnelheidschakelaar met uit-van-synchrone discontinutiesDit probleem werd opgelost door de ABR stitching edge cases correct te behandelen.

* Zendesk #19232 - De toepassing die TVSDK 1.4.18 gebruikt, gedraagt zich vreemd op oudere versie van Amazon OS 4Dit probleem is opgelost door het maken van de verborgen webweergave in het initialisatieproces van de TVSDK-speler te verwijderen om conflicten te voorkomen met apparaten die Android Webview niet ondersteunen.

* Zendesk #19585 - Langzaam afspelen bij adaptieve bitsnelheidovergang.
Als tijdens de ABR-schakelaar het nieuwe profiel een andere audiosamplefrequentie heeft dan het huidige profiel, wordt het afspelen snel of langzaam. De reden hiervoor is dat de videopresentator niet op de hoogte wordt gesteld van het feit dat de audio-indeling is gewijzigd.
Dit probleem is opgelost door ervoor te zorgen dat de berichtmarkering op de juiste plaats is ingesteld.

* Zendesk #19683 - SAP DAI playback - Geen audio voor een paar seconden.
In verschillende gevallen in de logica van TVSDK werd RENDITION_TIMEOUT_THRESHOLD, toen de tijdstempel van twee vertoningssegmenten werd vergeleken, gebruikt als een aanvaardbaar waardebereik, omdat de tijdstempel niet altijd kan worden vergeleken met een verschil van 0 ms. Als de tussenruimte binnen de waaier van RENDITION_TIMEOUT_THRESHOLD is, veronderstelt de veronderstelling dat het een gelijke is.

RENDITION_TIMEOUT_THRESHOLD werd geplaatst aan 100ms, maar het bleek ontoereikend voor bepaalde stromen. Dit probleem is opgelost door de RENDITION_TIMEOUT_THRESHOLD te verhogen tot 200 ms.

* Zendesk #19699 - TVSDK slaagt er niet in om tussen VTT ondertitelsporen te schakelen. Dit probleem werd opgelost door de spelerstortplaats te maken en manifest opnieuw te laden wanneer een spoor verandert en door het UTF8 probleem van de koordomzetting te verbeteren dat de dubbel-byte WebVTT de spoornamen van de ondertitel beïnvloedde.

* Zendesk #19717 - CC-opties geven een probleem weer. Dit probleem is opgelost door de Unicode-tekenreeks correct af te handelen.

* Zendesk #19910 - TIT2 ID3-tags niet gedetecteerdDit probleem is opgelost door meer volledige ondersteuning te bieden voor ID3 v2.4-tekenreekscoderingen en door ondersteuning te bieden voor ID3 v2.3.

* Zendesk #20135 - De TVSDK activeert meerdere onComplete voor VOD-inhoud.
Dit probleem is opgelost door de gebeurtenislistener post_roll_complete op de juiste plaats toe te voegen in plaats van met het volledige hoofdlettergebruik van de gebeurtenis status wijzigen.

**Versie 1.4.19 (1521)**

* Zendesk #4180 - De TVSDK past HDCP niet toe.
   * Dit is een gedeeltelijke oplossing voor dit kaartje en behandelt slechts de kwestie voor apparaten van het schild NVidia.
U moet de correct geïmplementeerde HDCP-detectie-API in het Nvidia-schild gebruiken om de HDCP-status dynamisch bij te houden.

* Zendesk #18358 - De TVSDK bevriest op bitsnelheidschakelaar met discontinuïteit buiten de synchronisatie.
   * Deze kwestie werd opgelost door een nieuwe waarschuwing toe te voegen om de discontinuïteit van PTS te ontdekken en door de controle van PTS te dwingen om het zoeken naar het correcte segment voor elke schakelaar ABR opnieuw te doen.
Om de bevriezing te bevestigen, zou de vraag aan de mediaPlayer.setCustomConfiguration methode forcePTSCheckForABR als argument moeten omvatten.

* Zendesk #19038 - Geen live stream op Asus Zenpad 10.

   Dit probleem is opgelost door de media-codec-informatie vooraf te laden, zodat u de functie niet tijdens runtime opnieuw hoeft te starten.

* De volgende kwesties zijn hetzelfde als Zendesk #19038:
   * Zendesk #19483 - De TVSDK loopt vast op het Intel-platform.
   * Zendesk #19171 - Crashes on Asus Memo Pad 7 with Android 5.0.

**Versie 1.4.18 (1503)**

* Zendesk #3324 - Rapportage voor primetime-advertenties houdt geen onderbrekingen bij wanneer er geen advertentiemedia in een VMAP aanwezig zijn.
Wanneer een advertentie-einde leeg is, werden de gebeurtenissen voor het starten en bijhouden van een advertentie niet gepingeld. Dit probleem is opgelost door het verzenden en afbreken van startpagina&#39;s op lege advertentieafbrekingen, zoals VMAP AdBreak, met een geldig AdSource-knooppunt.

* Zendesk #18229 - SetCCVisiblity(VISIBLE) wordt genegeerd na aanroep van MediaPlayer.reset() Dit probleem is opgelost door setCCVisibility(Visibility.INVISIBLE) toe te voegen; naar de reset() functie in de MediaPlayer klasse.

* Zendesk #18328 - Het probleem met gedropt frame op 2e gen-apparaten van Amazon Fire TV voor de inhoud met 60FPSTDit probleem is opgelost door de gecodeerde FPS toe te passen voor de besluitvorming tijdens de slaaptijd en met een beter gecodeerde FPS-voorspellingslogica.

**Versie 1.4.17 (1472)**

* Zendesk #2231 - de Fout die van het halen van manifest niet beschikbaar in MediaPlayerNotificationDeze kwestie is teruggekeerd door het antwoordlichaam van manifest te omvatten wanneer er een parseringsfout is.

* Zendesk #17703 - VideoEngineView verhindert geen schermafbeeldingen tijdens videoplaybackDe setSecure methode is sinds API 17 beschikbaar, maar omdat API 17 4.2, 4.2.1 en 4.2.2 behandelt, is het niet bekend welke een uitzondering zal werpen of of het apparaat specifiek is. Dit probleem is opgelost door VideoEngineView.setSecure in de catch-expressie try te plaatsen.

* Zendesk #17919 - Inhoud zoeken veroorzaakt hartslagfoutEen ongeldige fout van de Positie van inputgegevens kwam voor als resultaat van de hartslagvraag die werd geproduceerd toen het zoeken na de pre-rol werd begonnen. Dit probleem is opgelost.

**1.4.16a** (1454a)

* Zendesk #18215 - Sommige AES-streams kunnen niet worden geladen.
Dit probleem is opgelost door de grootte van de DRM-metagegevens van het profiel te controleren voordat de AES-sleutel werd geladen.

**Versie 1.4.16 (1454)**

* Zendesk #3875 - Tab S loopt vast tijdens het afspelenDe afhankelijkheid van OKHTTP bij Auditude voor CRS wordt omgekeerd, omdat TVSDK nu rechtstreeks httpurlconnection in plaats van curl gebruikt. Het probleem werd opgelost door uitzonderingen vrij te maken voordat een andere JNI-oproep werd gedaan.

* Zendesk #4487 - het Volgen Lineair Kanaal van InhoudHet probleem werd opgelost door het re-initialiseren van videohartslagtrekker tijdens een lineaire stroomplaybackzitting toe te staan.

* Zendesk #17919 - Android - content seek veroorzaakt hartslagfoutHet probleem wanneer de hartslag in een foutstatus is wanneer er een zoekopdracht in een hoofdstuk is uitgevoerd, is opgelost.

* Zendesk #18053 - Adobe Primetime loopt vast bij MarshmallowDe TVSDK crashte op Android M OS toen de TVSDK-bibliotheek neoncode gebruikte die de YUV -> RGB-kleurconversie uitvoert. Het probleem is opgelost door de functies die dit probleem veroorzaken bij te werken met de niet-neonversie van de code.

* Zendesk #18072 - Android M - Toepassing loopt vastWanneer wordt gecontroleerd of het profiel en het niveau worden ondersteund, treedt een crash op wanneer MediaCodecList en MediaCodecInfo API&#39;s worden aangeroepen. Het probleem is opgelost door tijdelijk werk te leveren door alle codec-informatie van tevoren te laden, zodat deze API&#39;s niet alleen hoeven te worden aangeroepen wanneer codec-informatie nodig is.

* Zendesk #18074 - Arabische ondertitels die niet werken op Nexus met Android 6.0 Het probleem is opgelost door ondersteuning te bieden voor CTS-lettertypetoewijzingen voor Android.

**Versie 1.4.15-update (1438)**

* Zendesk #17437 - Lange vertraging bij het opstarten van VOD-inhoud met sommige AES-streams.
Als u dit probleem wilt verhelpen en meerdere sleutels in manifest worden weergegeven, downloadt u alle AES-toetsen parallel.

**Versie 1.4.15 (1435)**

* Zendesk #4278 - Glitches op Android stellen bovenste vakken in als Adaptieve bitsnelheid verandert (ABR).
De oplossing was het toevoegen van ondersteuning voor naadloze ABR-switch met de nieuwste Android-mediacode.

* Zendesk #17063 - Calling mediaPlayer.reset() veroorzaakt een fout bij het opnieuw instellen van de video-engine.
De oplossing bestond erin de oorspronkelijke MediaErrorCode van VideoEngineExceptions op te nemen bij het verzenden van ErrorEvents.

* Zendesk #17130 - Een korte maar opvallende pauze bij het wijzigen van de bitsnelheid die wordt gezien op FireTV.
(Hetzelfde als #4278 hierboven) De oplossing was het toevoegen van ondersteuning voor naadloze ABR-switch met de nieuwste Android-mediacode.

* Zendesk #17666 - Aanvullende advertentiemarkeringen, Onverwachte of Geen advertenties bij het hervatten van inhoud.
De oplossing was een probleem tijdens het uitvoeren van prepareToPlay op video-on-demand (VOD)-inhoud. De eerste zoekactie wordt uitgevoerd op de lokale tijd in plaats van op virtuele tijd.

* Zendesk #17437 - Lange vertraging bij het opstarten van VOD-inhoud met sommige AES-streams.
De oplossing was om alle AES sleutels parallel te downloaden wanneer de veelvoudige sleutels in manifest worden vermeld.

* Zendesk #17851 - Android TV - Black Frame tijdens ABRTe correctie bestond uit het opgeven van KEY_MAX_WIDTH en KEY_MAX_HEIGHT om adaptief afspelen mogelijk te maken.

**Versie 1.4.14 (1415)**

* Zendesk #3875 - Tab S loopt vast tijdens het afspelen.
Er is een extra correctie vereist om te voorkomen dat het programma vastloopt.

* Zendesk #17245 - Fallback op Android TV werkt niet.
Probleem verholpen waarbij het afspelen vastloopt als fallback is ingeschakeld en het VMAP-antwoord een leeg ad-einde heeft.

**Versie 1.4.14 (1412)**

* Zendesk #17245 - Fallback op Android TV werkt niet.
Een beperking voor het uitschakelen van creatief opnieuw verpakken op fallback-advertenties is verwijderd.

**Versie 1.4.13 (1388)**

* Zendesk #3502 - HLS cliënt gebaseerde failoversteun tijdens een ad breakAllow failover aan belangrijkste manifest wanneer het bijwerken van levende profielfout tijdens een onderbrekingsperiode voorkomt.

* Zendesk #3875 - Tab S loopt vast tijdens het afspelen. Gebruik een bibliotheek van derden om het conflict tussen HttpUrlConnection en cURLm op te lossen.

* Zendesk #4450 - kwestie die de gegevens van douanemeta voor één enkele plaatsing in een inhoudsoplosser plaatstVoeg een zetter aan de montages van de Kans toe.

**Versie 1.4.12 (1388)**

* Zendesk #2751 - CSAI en CRS | Verbeteren: Dynamische elementen in bepaalde URL&#39;s van mediabestanden verwerken.
Bijgewerkte Creative Repackaging Service voor het correct verwerken van advertenties met dynamische creatieve URL&#39;s.

* Zendesk #3965 - Het schakelen terug naar normaal playback van trickplay resulteert in een sprong voorwaarts alvorens met playback te beginnen.
   * Fix omvat TVSDK die de tijd vóór de tariefverandering terugkeert tot alle variabelen worden bijgewerkt, in plaats van het proberen om GetStreamTime te berekenen.
   * Correctie van crash bij wijzigen van speelsnelheid voor truc aan het einde van de stream.
   * Correctie van huidige tijdberekening tijdens truc-play.

* Zendesk #3978 - Trickplay bij 8x en 16x bevriest vaak.
   * Kies altijd het truc-spelprofiel met de laagste bitsnelheid om constant bufferen te voorkomen.
   * Gebruik een hogere waarde voor het overslaan van het frame voor een hoge fel-afspeelsnelheid.
   * Los een kwestie op die de buffer na het bereiken van zijn doellengte tijdens kunstspel blijft groeien.

* Zendesk #3992 - Aanvullende Trickplay-snelheden.
TrickPlay is bijgewerkt om snelheden hoger dan 16x te accepteren; +/- 32, +/-64 en +/-128 zijn nu ook toegestaan.

* Zendesk #4007 - Het GEOB-object interpreteren als onderdeel van de tijdlijnmetagegevens (Android en Web).
Toegevoegde setByteArray- en getByteArray-API.

* PTPLAY-7301 - Onmiddellijk aan begin bij het Willekeurige Punt van de Toegang.
Instant On is bijgewerkt om een startpunt van niet nul toe te staan.

**Versie 1.4.11 (1363)**

* Zendesk #2076 - Frequent schokkerig wanneer het spelen van video op Motorola Xoom met Android 4.0.3Toegevoegde apparaten om lijst toe te staan om hen te verhinderen om high-profile inhoud te spelen.

* Zendesk #2197 - `[Ads]` Tracking and error dispatch OperationFailedEvent met waarschuwingsmelding.

* Zendesk #3304 - VAST 3.0- `[ERRORCODE]` macro niet gevuld
   * foutcode 400 wordt weergegeven als deze inline is en slecht creatief is.
   * `[ERRORCODE]` macro wordt URL-gecodeerd

**Versie 1.4.10 (1354)**

* Zendesk #2941 - Levende activa hebben geen &quot;0&quot;in zoekbare waaierEerder was er een 3 segmentbuffer toen het zoeken aan het begin van een Levende stroom, nu is het mogelijk om tot het zeer begin van een levende stroom (d.w.z. het begin van het eerste segment) te zoeken.

* Zendesk #3169 - Update reference player with Adobe Analytics integrationThe reference player has been updated with the Adobe Analytics library as an example implantation.
* Zendesk #3299 - Onverklaarbaar gedrag bij het spelen van een truc
   * Het probleem waarbij het terugkeren naar de afspeelstatus na het stoppen van truc enkele seconden kon duren (soms 25+ seconden), is opgelost.
   * Probleem verholpen waarbij het aanroepen van een truc een tweede keer op dezelfde media wordt afgespeeld, kan ertoe leiden dat de stream op het huidige moment vastloopt.
* Zendesk #3433 - Android en Flash - Problemen met ondertitels

GetLine voor WebVTT voldeed niet aan &lt;CR>&lt;LF> aangepaste lengte voor een pakket; het laatste bijschrift kan tekens uit vorige bijschriften bevatten.

* PTPLAY-6243 - Verbeter verwijzingsspeler om te vangen zuivert informatie

De Android-voorbeeldspelers zijn verbeterd en hebben nu een optie waarmee u foutopsporingslogboeken kunt inschakelen en de resultaten via e-mail kunt verzenden. Deze optie vindt u onder het menu Logboek in de referentiespeler.

**Versie 1.4.9 (1332)**

* Zendesk #2649 - Buffer Complete treedt op voordat de eerste buffer vol is

Na een zoekactie is het mogelijk dat de videoengine de status PLAYING instelt voordat de videopresentator klaar is om te worden afgespeeld. Vindt plaats wanneer de bufferstatus hoog is voordat wordt gezocht. Oplossen door de video-engine een melding te geven van een lage bufferstatus. Bij een lage bufferstatus van de video-engine leidt het aanroepen van Play tot een statuswijziging in BUFFERING in plaats van PLAYING. Het afspelen wordt hervat wanneer de status verandert in AFSPELEN.

* Zendesk #2846 - Aanvraag tot verbetering: Verstrek capaciteit om verschillend user-agent koord voor vraag te plaatsen die door de bibliotheek van de Audittegraad wordt gemaakt

Er is een nieuwe API toegevoegd om de gebruikersagent in te stellen voor gerelateerde aanroepen, zoals auditudeSettings.setUserAgent(&quot;user/agent&quot;). Als geen gebruikersagent wordt geplaatst, zal het gebrek worden gebruikt. Dit beïnvloedt slechts de gebruikersagent voor verwante vraag, is de gebruikersagent voor media vraag onveranderd die &quot;Adobe Primetime&quot;+&lt;default useragent> is.

**Versie 1.4.8 (1324)**

* Zendesk #1218 - 106000.33 Fout bij lokaal ... Als ladingsmanifest in FragmentedHTTPStreamer::ThreadParseManifest () ontbreekt, controleer of is het domein URL localhost en zo, verander domein in 127.0.0.1 en herinner ThreadParseManifest.
* Zendesk #3072 - Automatische omschakeling naar lagere bitsnelheden. Veranderde berekening van de bufferlengte om 0 PTS nuttige lading over te slaan.
* Zendesk #3168 - WebVTT ondertitels slechts getoond voor eerste 10 sec.
* Zendesk #3193 - Verzoek om een API voor profielwijziging in TVSDK, PlaybackEventListener.onProfileChanged() is toegevoegd.

**Versie 1.4.7 (1311)**

* Zendesk #2197 - Tracking and errors. Toegevoegde melding voor element kan manifest niet laden
* Zendesk #2575 - PSDK negeert MARK aangepaste in-stream advertentie vóór video
* Zendesk #2719 - Win Dood met auditieve advertenties, vast baken volgen wanneer omgeleid naar de relatieve URL in auditude plugin
* Zendesk #2760 - DISCONTINUITY-tag genegeerd tijdens TrickPlay-modus
* Zendesk #2805 - Speler crashte bij Begin van afspelen, zelfde moeilijke situatie zoals Zendesk #2719
* Zendesk #2817 - Android-speler - De speler loopt soms vast en stopt met afspelen, gecorrigeerd door het uitbreiden van de decodebuffers van 2,0 tot 3,0 seconden
* Zendesk #2839 - Does Adobe Primetime PSDK support ARMv8 chipsets?, added fix for crash found on Galaxy S6.
* Zendesk #2885 - Afspelen van Auditude Crashing, zelfde probleem als Zendesk #2719
* Zendesk #2895 - Live HLS mislukt na 10 minuten afspelen
* Zendesk #2925 - Terugkoppeling betreffende de bouwstijl van Android (1.4.5), op bepaalde apparaten wanneer wij het pakket aan de inputrij in rij plaatsen, als PTS negatief is, gaat de decoder in een vreemde staat dat wij altijd een negatieve outputPTS voor toekomstige pakketten krijgen. Met de correctie wordt de invoer-PTS op nul ingesteld als dit probleem wordt voorkomen.
* PTPLAY-4645 - Schakel RC4 cipher ondersteuning in openssl uit. Er zijn bekende explosies voor RC4. Dit betekent dat als wordt geprobeerd om met een server te verbinden die slechts RC4 steunt, het zal ontbreken.

**Versie 1.4.6 (1282)**

* Zendesk #2192 - Bitsnelheid vermindert niet altijd in slechte netwerkvoorwaarden, die door snelle schakelaarimplementatie te verwijderen worden bevestigd.
* Zendesk #2631 - Arabische ondertitels op Android: Tekst op meerdere regels wordt afgekapt weergegeven. De tekst wordt gecorrigeerd door de tekengrootte voor Arabische lettertypen aan te passen.
* Zendesk #2844 - Het bufferen op Nota 4 en de downloadtijd van het Fragment is niet nauwkeurig.

Deze kwestie werd opgelost door latentie tussen videosegmentdownloads in bandbreedteberekening toe te voegen en het hebben van de logica van de downloadtijdberekening de volledige tijd van de verzoekcyclus gebruiken.

* Zendesk #2908 - Arabische ondertitels die niet werken op Nexust 5, 6 en 7, die worden gecorrigeerd door 2 extra fallback-lettertypen toe te voegen voor Arabische scripts.
* PTPLAY-4627 - update Nielson appsdk aan versie 1.2.3.7
* PTPLAY-5084 - Live Master Manifest update failover-ondersteuning

**Versie 1.4.5 (1248)**

* Zendesk #1757 - Alleen audio afgespeeld of speler crasht voor een bepaald videobitsnelheidprofiel, Nexus 4 en Nexus 7 zijn hersteld
* Zendesk #2072 - TimedMetadata for AdEvent bevat niet de volledige URL alleen &quot;http&quot;
* Zendesk #2192 - Bitsnelheid is niet altijd lager in slechte netwerkomstandigheden
* Zendesk #2256 - Toegang tot stramienafspeellijst, bijgewerkte PSDK om gebeurtenissen met tijdedMetadata te verzenden voor geabonneerde tags op de stramienafspeellijst.
* Zendesk #2269 - Twee verschillende ondertitelingstalen verschijnen op het scherm tezelfdertijd met WebVTT
* Zendesk #2417 - Speler die ondertitels probeert te downloaden alvorens playbackbegin, WebVTT gebruikte de verkeerde variabele van het segmentaantal voor segmentaantalaanpassing. Er zou alleen een fout optreden voor media waarvoor de segmentindexen nul waren.
* Zendesk #2470 - PSDK keert niet terug uit de SUSPENDED status wanneer de bitsnelheidverandering zich voordoet na de suspensie. In een speciale situatie wanneer slim zoeken wordt aangeroepen door RestoreGPUResource (de terugzetspeler wordt uitgeschakeld) en streamswitch die daarvoor wordt gedetecteerd, kan Smart seek niet voltooien en resulteren in constante buffering.
* Zendesk #2451 - Closed captioning &#39;bottom inset&#39;, added &#39;bottomInset&#39; parameter to caption code
* Zendesk #2480 - het onbruikbaar maken van HTTP 302 herdirect optimalisering, Toegevoegde steun voor het plaatsen van useRedirectedUrl bezit
* Zendesk #2486 - Derde partijenbakens
* Zendesk #2547 - Arabische ondertitels: Tekst moet rechts worden uitgelijnd

**Versie 1.4.4 (195)**

* Zendesk #1158 - Het afspelen mislukt bij Huawei Valiant (Y301A1)
* Zendesk #1709 - Onjuiste mediagrootte en uitgerekte video
* Zendesk #1757 - Alleen audio die wordt afgespeeld nadat tussen streams met identieke spa/pps-gegevens is geschakeld
* Zendesk #2095 - HTTP 307 status (omleiding) zorgt ervoor dat Adobe Player het afspelen stopt
* Zendesk #2126 - Ontbrekende gebeurtenis TimedMetaData voor laatste ADEVENT, Geabonneerde markeringen die bestaan nadat het laatste segment niet aan PSDK van AVE werden gemeld
* Zendesk #2227 - Lockups in VideoEngine nativeReset en nativePause
* Bug #3921755 - OpenSSL-bibliotheekupdate naar versie 1.0.1L

**Versie 1.4.3 (1173)**

* Zendesk #1591 - RENDITION_M3U8_ERROR
* Zendesk #1870 - Ondertiteling ingeschakeld en uitgeschakeld
* PTPLAY-1818 - Terugspoelen de speleinden van de truc bij de advertentie in plaats van het terug te spoelen voorbij het
* PTPLAY-2736 - een eerder getoonde WebVTT titel wordt getoond op het scherm wanneer een stroom met WebVTT het spelen voltooit
* PTPLAY-3773 - een middenrol wordt niet gespeeld wanneer de stroom playback na de advertentiepositie wordt begonnen

**Versie 1.4.2**

* Zendesk #1561 - HLS client based failover support in primetime. Zal de tijd van de programmadatum gebruiken om failover te richten
* Zendesk #1590 - LoadInfo.MediaDuration is altijd 0 (niet vast voor audio-slechts)
* Zendesk #1626 - Potentieel geheugenlek in speler. Geen echt geheugenlek. Het probleem is ontstaan toen NotificationHistory de laatste 1000 meldingen heeft opgeslagen. Dit probleem is teruggebracht tot 100.
* Zendesk #2192 - Bitsnelheid is niet altijd lager in slechte netwerkomstandigheden

**Versie 1.4.1 (1121)**

* Zendesk #1951 - Lockup in VideoEngine.nativeReset() op 4.0.x-apparaten
* Zendesk #2064 - Native Crash SIGSEGV op specifieke Android-apparaten op basis van intel
* Zendesk #2075 - Lockup in VideoEngine.nativeReleaseGPUResource op 4.0.x-apparatenOpmerking: Deze build is ***vereist** voor ondersteuning van Android 5.0 (Lollipop)
* Zendesk #1513 - Ondersteuning voor Android Lollipop
* Zendesk #1709 - Onjuiste mediagrootte en uitgerekte video
* Zendesk #1871 - WebVTT-bijschriften verdwijnen af en toe en verschijnen opnieuw wanneer een livestream met WebVTT-bijschriften wordt weergegeven
* Zendesk #1996 - Geen tijdlijnmarkeertekens weergegeven in PSDK 1.4.0
* Zendesk #2046 - Crash with PSDK 1.4.1.1113, fixed crash for live streams when no ads returned from auditude
* Bug #3769657 - Update de versie van krulling aan 7.38.0
* PTPLAY-1575 - Wanneer het afspelen van ABR met audio slechts stroom dan schakelaars aan audio/videostroom begint, geeft de video nooit terug terwijl de audio verdergaat
* PTPLAY-2499 - Update aan OpenSSL aan versie 1.0.1j om recente kwetsbaarheden te richten
* PTPLAY-2632 - Video wordt niet hersteld na mid-roll Ad voltooid op Android Lollipop
* PTPLAY-2678 - Videozalen tijdens live levensduurtests op Android Lollipop

**Versie 1.4.0**

* Zendesk #1024 - Functie voor het verwijderen van advertenties uit de stream via manifest
* Zendesk #1293 - Closed Caption Track Selection Issue.
* Zendesk #1590 - LoadInfo.MediaDuration is altijd 0, mediaDuration toont nu de correcte waarde.
* Zendesk #1629 - speler/app crasht aan het einde van de afspeelbewerking op Galaxy S4
* Zendesk #1674 - ClosedCaption Niet zichtbaar, corrigeer de weergave van 708 bijschriften wanneer 0x03 ETX-codes ontbreken.
* PTPLAY-2157 - de Standaard gesloten Captioning stijlen zijn teruggekeerd door getters zelfs als na een verschillende stijlen is geplaatst en visueel op de stroom geverifieerd. In de stijleigenschappen van Closed Caption wordt nu de waarde weergegeven waarop deze zijn ingesteld.

## Bekende problemen in 1.4 {#known-issues-in}

**Versie 1.4.31**

* PTPLAY-16803 - Gesloten Bijschrift werkt niet met alleen audio-inhoud omdat het bijschriftsysteem video nodig heeft om te werken. Zonder video is er geen viewport-dimensie en zonder viewport-dimensie kunnen we geen afbeeldingen voor bijschriften weergeven.
* PTPLAY-1634 - De zelfde Geabonneerde markering heeft verschillende timestamps in verschillende levende vensters. Wanneer het live venster wordt verplaatst, moet dezelfde tag in de tags dezelfde tijdstempels hebben. Soms hebben zelfs dezelfde tags echter verschillende tijdstempels.
* PTPLAY-3197 - Crash with signaal 11 SIGSEGV error on Acer Iconia device after ~ 1 hour of continue playback
* PTPLAY-3310 - Met wat lagere bitsnelheidaudio, wordt de audio schokkerig/schokkerig op Acer Iconia
* PTPLAY-3355 - WIN DEATH crasht op Motorola Xoom met 4,0,x na ~ 1 uur ononderbroken afspelen.
* PTPLAY-3557 - Terugspoelen bij een ad-break veroorzaakt de stroom om te voltooien
* PTPLAY-7079 - het Venster van de Playback op android cliënt werkt niet met Veilige Stop/Harde Stop
* Bug #3760144 - De resolutie kan veranderen of lijkt te bewegen wanneer de stroom op sommige apparaten zoals Kindle Fire 7 en Samsung Galaxy Nexus wordt gepauzeerd. Enkel waarneembaar onder nauwgezet toezicht
* Bug #3761170 - seekToLocal in Live met advertenties kan niet terugzoeken in advertentie-inhoud. Het is de beste manier om de huidigeTijd-API&#39;s voor live streams te gebruiken
* Bug #3763370 - Live streams met advertenties laten soms twee advertentiemarkeringen bij elkaar zien wanneer er slechts één zou moeten zijn. Deze advertentiemarkeringen vertegenwoordigen dezelfde advertentie en slechts één zal spelen
* Bug #3763373 - De advertentiemarkering kan kort verdwijnen wanneer u voorbij een advertentie in VOD-streams zoekt. De advertentiemarkering wordt hersteld en er is geen ander negatief effect op de tijdlijn
* Sommige apparaten kennen afspeelproblemen. Zie [Bekende apparaatproblemen in 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Referentie-implementatie - Stenen wordt niet geïmplementeerd in de voorbeeldtoepassing
* Op sommige Android-tv-apparaten kan een zwart frame worden weergegeven als de decoder opnieuw wordt ingesteld op de volgende overgangspunten:
   * in- en uit-speelmodus
   * schakelen tussen audiotracks met late binding
   * van een advertentie naar de hoofdinhoud.

**Versie 1.4.23**

* Closed Caption werkt niet met alleen-audio inhoud omdat het bijschriftsysteem video nodig heeft om te werken. Zonder video is er geen viewport-dimensie en zonder viewport-dimensie kunt u geen afbeeldingen voor bijschriften weergeven.
* Vanaf versie 1.4.23 biedt de TVSDK geen ondersteuning voor Gingerbrood OS 2.3. De reden hiervoor is dat de TVSDK de volgende persoonlijke Android-bibliotheken heeft gebruikt om hardwareinformatie te verzamelen over apparaten met het Gingerbrood-besturingssysteem:

   * `libstagefright.so`
   * `libcutils.so`

In de Android N-release heeft Google de toegang tot deze privébibliotheken verwijderd. Het Gingerbrood OS is momenteel wereldwijd goed voor minder dan 1% van het marktaandeel van Android OS, dus na versie 1.4.23 wordt het Gingerbrood OS niet meer ondersteund door de TVSDK.
Wanneer u versie 1.4.23 (inclusief ondersteuning voor Android N) of hoger gebruikt:
* Werk uw apps bij voor gebruik van minSdkVersion versie 11.
* Als uw eindgebruiker OS 2.3 in werking stelt, dan is de versie van SDK lager dan minSdkVersion van de toepassing. De installatie of upgrade van de toepassing wordt door het systeem afgebroken.
* Als uw eindgebruiker een versie uitvoert die hoger is dan OS 2.3, wordt de toepassing op de juiste wijze geïnstalleerd.

Als u minSdkVersion bijwerkt:

* Als uw eindgebruiker OS 2.3 uitvoert, wordt de toepassing geïnstalleerd maar het afspelen werkt niet.
Dit geldt zowel voor de update als voor de nieuwe installatie.
* Als uw eindgebruiker een systeem uitvoert dat hoger is dan OS 2.3, wordt de app correct geïnstalleerd en wordt de inhoud correct afgespeeld.

**Versie 1.4.22**

* De vroege uitgang uit advertenties werkt niet met sommige mid-roll advertenties wanneer de splice-out en splice-in tag te dicht bij elkaar zijn.

**Versie 1.4.2**

* Terugspoelen bij een advertentieeinde leidt tot voltooiing van de stream.

De Media Player verzendt MediaPlayerState.Complete onjuist tijdens de terugspoelbewerking voor Trick Play wanneer een ad-grens wordt bereikt. De speler moet deze gebeurtenis negeren in de truc-afspeelmodus, anders wordt de status correct verwerkt in de SDK.

**Versie 1.4.0 (1086)**

* PTPLAY-1634 - de zelfde Geabonneerde markering heeft verschillende timestamps in verschillende levende vensters. Wanneer levende vensters zich bewegen, zou de zelfde markering in elk van hen zelfde timestamps moeten hebben. Soms hebben zelfs dezelfde tags echter verschillende tijdstempels.
* PTPLAY-2541 - COMPONENT_CREATION_FAILURE wordt soms gezien na verscheidene schakelaars aan/van de afwisselende stroom in stroomonderbrekingen
* Bug #3726865 - Als een LBA-stream met multibitsnelheid vanuit een alleen-audiostream start, wordt de video niet weergegeven als naar een audio- of videostream wordt geschakeld. Vanaf een audio- of videostream wordt dit probleem niet weergegeven en kan worden geschakeld tussen audio- en audio- of videostreams
* Bug #3760144 - De resolutie kan veranderen of lijkt te bewegen wanneer een stroom wordt gepauzeerd op sommige apparaten zoals Kindle Fire 7 en Samsung Galaxy Nexus. Enkel waarneembaar onder nauwgezet toezicht
* Bug #3761170 - seekToLocal in Live met advertenties kan niet terugzoeken in advertentie-inhoud; het is aan te raden de huidigeTime-API&#39;s te gebruiken voor Live streams
* Bug #3763370 - Live streams met advertenties laten soms twee advertentiemarkeringen bij elkaar zien wanneer er slechts één zou moeten zijn. Deze advertentiemarkeringen vertegenwoordigen dezelfde advertentie en slechts één zal spelen
* Bug #3763373 - De advertentiemarkering kan kort verdwijnen wanneer u voorbij een advertentie in VOD-streams zoekt. De advertentiemarkering wordt hersteld en er is geen ander negatief effect op de tijdlijn
* Sommige apparaten kennen afspeelproblemen. Zie [Bekende apparaatproblemen in 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14)voor meer informatie.
* Referentie-implementatie - Stenen wordt niet geïmplementeerd in de voorbeeldtoepassing.

## Bekende apparaatproblemen in 1.4 {#known-device-issues-in}

| Apparaat | Chipset | Probleem | Oorzaak | Workaround |
|--- |--- |--- |--- |--- |
| Droid X | TI OMAP3 | ABR-vertraging wordt verwacht omdat de decoder opnieuw wordt gestart. |  |  |
| HTC Desire (anders dan HTC Desire HD) | QSD8250 | Kan video niet afspelen. Returns VIDEO_PROFILE_NOT_SUPPORTED error. | Desire biedt geen juiste HW-decoder. Het geeft Stagefright&#39;s SW decoder. | Start het apparaat opnieuw. |
| HTC EVO 4G | QSD8650 | Geen HW-decoder. | Qualcomm heeft geen HW-decoder. | Upgrade naar Android 4.x. |
| Kindle FireSystem versie 6.0 | TI OMAP4 | Hiermee worden HLS-streams niet afgespeeld. Video op AIR werkt niet. |  | Upgrade naar systeemversie 6.3. |
| Kindle Fire HD | TI OMAP4 | Kan een status activeren waarin video niet kan worden afgespeeld. Retourneert fouten VIDEO_PROFILE_NOT_SUPPORTED en UNRECOVERABLE_ERROR. | De HW-decoder wordt onherstelbaar wanneer de toepassing de HW-decoder niet volledig uitschakelt, bijvoorbeeld na een crash. gebeurt ook op native apps op het apparaat. | Start het apparaat opnieuw. |
| Kindle Fire HD 8.9 | Snapdragon 800 | AVE crasht na meerdere ABR-switches. |  |  |
| Motorola Atrix | Tegra2 | Algemene prestatieproblemen met AVE in tegenstelling tot AIR. Audio/video wordt niet gesynchroniseerd en het afspelen van video loopt vast na het afspelen tussen 9 en 15 minuten. Crashes. | Mogelijk gerelateerd aan openGLES die we inschakelen op AIR. Wordt onderzocht. |  |
| Nexus 7 (tweede gen) | S4Pro APQ8064 (Qualcomm) | Het apparaat loopt vast wanneer een film langer dan 30 minuten wordt gepauzeerd. | Apparaatprobleem dat aan Google is gemeld. | De toepassing moet een time-out toepassen om geen lange pauzestatus toe te staan. |
| Nexus S (GB) | Vogelvogel | Kan geen video afspelen met HW-decoder. | Er is geen op Stagefright gebaseerde HW-decoder in Nexus S, dus voor Android 2.3 gebruiken we een SW-decoder. | Upgrade naar ICS. |
| Nexus S (ICS) | Vogelvogel | Soms flikkert video. | Onjuiste gegevens kunnen ertoe leiden dat de decoder in een slechte toestand raakt. | Start het apparaat opnieuw. |
| Nook-tabletAndroid-besturingssysteem: 2,3 | TI OMAP 4 | Video wordt niet afgespeeld en de app loopt vast. | StageFright wordt instabiel nadat de app een paar keer is uitgevoerd. Vraag aan mediaplayer::QueryCodecs hangt. | Start het apparaat opnieuw om de status te herstellen. |
| Samsung Galaxy ACE | Qualcomm MSM7227 | Kan SampleMediaPlayer-app niet installeren. | Gebruikt ARM v6 in plaats van de gemeenschappelijkere ARM v7 chipset. FP/AIR biedt geen ondersteuning voor dit apparaat. |  |
| Samsung Galaxy ACE2Android OS: 2.3.6. | NovaThor U8500 | Kan video niet afspelen. | Deze chipset is een onbekende decoder voor Android pre-ICS in AVE. |  |
| Samsung Galaxy S2 (GT-I9100) | Exynos | De videoprestaties zijn niet tot op gelijke voor dit apparaat. | De HW-decoder retourneert gedecodeerde frames met de verkeerde PTS. Het lijkt erop dat de decoder de decoderingstijd in plaats van de presentatietijd gebruikt. |  |
| Samsung Galaxy S2 GAndroid-besturingssysteem: 2.3.6. | TI OMAP4 | Crashes tijdens het starten van de video. |  | Upgrade naar Android 2.3.7 of 4.x. |
| Samsung Galaxy S3 (I747) | Qualcomm MSM8960 | Soms loopt de video vast en wordt alleen audio afgespeeld en reageert deze niet meer. |  |  |
| Samsung Galaxy S3 I747M | SAMSUNG_M2ATT | Video bevriest. | Onderzoek. |  |
| Samsung Galaxy Tab 1 v10.1 | Tegra 2 | De overgang MBR zou tot drie seconden kunnen vergen. | Als moeilijke situatie voor MBR crashes, beginnen wij decoder voor elke stroomschakelaar opnieuw, die tot drie seconden kan vergen. |  |
| Samsung Galaxy Y |  | Kan SampleMediaPlayer-app niet installeren. | Gebruikt ARM v6 in plaats van de gemeenschappelijkere ARM v7 chipset. FP/AIR biedt geen ondersteuning voor dit apparaat. |  |
| Xoom | Tegra | Een paar frames worden verwijderd voor het schakelen. De decoder wordt niet opnieuw gestart. | OMXAL-beperking. |  |

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html) .
