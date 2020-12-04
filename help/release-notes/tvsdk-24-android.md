---
title: Opmerkingen bij de release TVSDK 2.4.1 voor Android
seo-title: Opmerkingen bij de release TVSDK 2.4.1 voor Android
description: In de Release-notities bij TVSDK 2.4.1 voor Android worden de nieuwe en ondersteunde functies en de bekende problemen en beperkingen in TVSDK Android 2.4.1 beschreven.
seo-description: In de Release-notities bij TVSDK 2.4.1 voor Android worden de nieuwe en ondersteunde functies en de bekende problemen en beperkingen in TVSDK Android 2.4.1 beschreven.
uuid: 929fc577-e851-4e03-9201-13280cc6137a
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: a6dbcc4a-9e14-4452-9004-b39ed13fad6f
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 0%

---


# Opmerkingen bij de release van TVSDK 2.4.1 voor Android {#tvsdk-for-android-release-notes}

In de Release-notities bij TVSDK 2.4.1 voor Android worden de nieuwe en ondersteunde functies en de bekende problemen en beperkingen in TVSDK Android 2.4.1 beschreven.

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobe geeft TVSDK 2.4.1 voor Android uit.

Als u deze versie van TVSDK wilt gebruiken, moet u ervoor zorgen dat uw systeem voldoet aan de vereisten die worden beschreven onder [Systeemvereisten](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6).

Hier vindt u documentatie:

・ Online Help-systeem TVSDK 2.4 voor Android Help

・ [Javadocs TVSDK 2.4 voor Android Java API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

De Javadocs zijn de ultieme instantie, omdat ze automatisch rechtstreeks worden gegenereerd vanuit de TVSDK-broncode.

・ [C++ API-documentatie TVSDK 2.4 voor Android C++ API](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

Elke klasse van Java heeft een overeenkomstige C++ klasse, en de documentatie C++ bevat verklarend materiaal dan JavaDocs, zo raadpleeg de C++ documentatie voor een dieper inzicht in Java API.

・ Migratiehandleiding ([TVSDK 2.4 voor Android-migratiegids](../migration-guides/tvsdk-14-25-android.md))

In deze handleiding wordt uitgelegd wat u moet wijzigen om een toepassing op basis van TVSDK 1.4 te migreren naar een toepassing op basis van TVSDK 2.4.

## Nieuwe functies {#new-features}

TVSDK 2.4.1 voor Android biedt veel prestatieverbeteringen ten opzichte van eerdere versies. Het biedt een kijkervaring van hoge kwaliteit.

Deze versie bevat alle functies van versie 2.4 en 2.4.1 en er zijn geen functies verouderd.

Hier volgen de belangrijkste nieuwe functies van versie 2.4.1:

* Functies van HLS versie 4

   * **Video afspelen**  (afspelen, pauzeren, zoeken) met afspeelbesturingselementen voor live, lineaire en VOD-streams.
   * **Ondertiteling gesloten.** TVSDK kan 608/708 gesloten bijschriften weergeven met een aantal lettertypen, tekengrootten, kleuren en achtergrond. Het kan video&#39;s met roll-up titels en schakelaar tussen taalsporen ook steunen als die beschikbaar zijn.
   * **Trick play** modesupports snel voorwaarts en terugspoelen voor stromen HLS die I-Kaders gebruiken. Alle besturingselementen voor het afspelen van video werken op de inhoud. Langzame beweging (vooruit) is beschikbaar voor de externe afspeelmodus van video met een snelheid tussen 0 en 1.
   * **Met Adaptieve bitsnelheid (ABR)** kan de speler dynamisch selecteren welke versie van dezelfde inhoudsstream moet worden afgespeeld, op basis van het netwerk en andere voorwaarden. U kunt parameters dynamisch instellen of in het manifestbestand selecteren onder agressief, matig en conservatief selectiebeleid.
   * **Byte** rangschikt één enkel TS dossier om veelvoudige TS segmenten te bevatten.
   * **Alternatieve audio-renditionable** de speler om tussen beschikbare audiosporen te schakelen.
   * **ID3-ondersteuning.** TVSDK kan HLS-audio- en videostreams afspelen die ID3-audiometagegevens bevatten, zoals de artiest, titel en album.
   * **Failover. **TVSDK gebruikt strategieën om ononderbroken playback voort te zetten, ondanks mislukkingen van gastheerservers, playlist dossiers, en segmenten.
   * **Audio-doorvoer via meerdere kanalen (DD+).** TVSDK kan Dolby Digital Plus-audiogegevens (E-AC3) doorgeven voor ondersteuning van hardware.

* Functies voor inhoudsbeveiliging

   * **DRM voor HLS.** Alle video playback APIs werkt met gecodeerde videoinhoud die door Adobe Access wordt beschermd. De volgende DRM-functies worden ondersteund:

      * Licentie roteren
      * Toetsrotatie
      * Licentie in cache plaatsen
      * Beleidstijd
      * IV-rotatie

* **AES 128 Playback.** TVSDK kan geavanceerde HLS-inhoud van coderingsstandaard (AES) afspelen met een sleutellengte van 128 bits.
* **Protected HLS (PHLS)** verstrekt een beperkte reeks vooraf gebouwd beleid DRM, een ondergroep van wat Adobe Access verstrekt, om lichtgewichtDRM over HLS voor levende en stromen VOD toe te laten.

* Reclame/alternatieve inhoud en monetiekenmerken

   * **Volgen voor aan de serverzijde ingevoegde advertenties.** TVSDK kan advertenties bijhouden die zijn ingevoegd door de Adobe Cloud en de invoegservice. Het steunt lineaire advertenties in VAST2, VAST3, en formaten VMAP voor VOD en levende/lineaire stromen.
   * **Aangepaste HLS-tags.** TVSDK gebruikt zijn  `MediaPlayerConfig` klasse om het melden van de spelertoepassing mogelijk te maken wanneer er aangepaste HLS-tags in de stream verschijnen.
   * **Client-kant en invoeging.** De Auditude- en invoegbibliotheek werken samen met Adobe Auditude-servers om advertenties op dynamische, lineaire en VOD-posities op te lossen, zodat ze kunnen worden ingevoegd in live, lineaire en VOD-inhoud, op pre-, mid-roll- of post-roll-posities.
   * **Aangepaste en oplosbare versies.** Met de  `ContentResolver, OpportunityGenerator,` en  `MediaPlayerClientFactory` interfaces kunt u een aangepaste en/of alternatieve contentoplosser implementeren en een aangepaste opportuniteitsdetector registreren voor gebruik met TVSDK. De `TestAdResolver` en `AuditudeResolver` klassen verstrekken C++ voorbeelden om een inhoudsoplosser uit te voeren. U kunt een voorbeeld Javascript bij `samples/jspsdk/testapp/psdk.js` vinden.
   * **Consistent gedrag voor toevoegen.** Gebruik de  `AdPolicySelector` interface om consistent gedrag tussen alle spelers mogelijk te maken voor bewerkingen zoals zoeken en spelen wanneer advertenties in de inhoud aanwezig zijn. Als u niet uw eigen implementeert, gebruikt TVSDK `DefaultAdPolicySelector`.
   * **C3-advertenties verwijderen/vervangen.** Gebruik de juiste TVSDK API om aangepaste inhoudsbereiken te verwijderen en dynamisch nieuwe advertenties in te voegen zonder extra voorbereidend werk. Dit is handig wanneer live/lineaire inhoud wordt uitgezonden en vervolgens onmiddellijk op aanvraag beschikbaar wordt gesteld zonder opschoning.

Hier volgen de belangrijkste nieuwe functies versie 2.4:

* **Instant on voor VOD en** liveWhen you enable instant on, TVSDK initialiseert en buffert media alvorens playback begint. Omdat u meerdere `MediaPlayerItemLoader` instanties tegelijk op de achtergrond kunt starten, kunt u meerdere streams in buffer plaatsen. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen op het nieuwe kanaal onmiddellijk gestart. TVSDK 2.4 biedt ook ondersteuning voor Instant On voor live streams. De live streams worden opnieuw gebufferd wanneer het live venster wordt verplaatst.

* **Prestatieverbeteringen **De nieuwe TVSDK 2.4-architectuur biedt verschillende prestatieverbeteringen:

   * **Subsegmentatie**  - TVSDK verkleint verder de grootte van elk fragment om het afspelen zo snel mogelijk te starten.
   * **Parallel en gedownload**  - TVSDK prefetches plaatsen parallel aan het afspelen van de inhoud voordat de advertentie wordt afgebroken, zodat advertenties en inhoud naadloos kunnen worden afgespeeld.
   * **Lazy ad resolution**  - Met deze eigenschap, wachten wij niet op resolutie van niet pre-preroll advertenties alvorens playback te beginnen, zo verminderend de starttijd. API&#39;s zoals zoeken en spelen met truc zijn nog steeds niet toegestaan totdat alle advertenties zijn opgelost.

* **Afspelen van MP4-inhoud**

Deze versie van TVSDK ondersteunt het afspelen van MP4 als hoofdinhoud.

* **Blijvende netwerkverbindingen**

TVSDK onderhoudt een reeks herbruikbare netwerkverbindingen, zodat het niet de overheadkosten van het creëren van en het vernietigen van een netwerkverbinding voor elke netwerkverzoek draagt.

* **Op resolutie gebaseerde uitvoerbeveiliging**

Met deze functie worden afspeelbeperkingen aan specifieke resoluties gekoppeld, zodat u over fijnere korrelige DRM-besturingselementen beschikt.

* **Steen spelen met adaptieve bitsnelheid (ABR)**

Met deze functie kan TVSDK schakelen tussen iFrame-streams in de truc-afspeelmodus. U kunt niet-iFrame-profielen gebruiken om met lagere snelheden te bedriegen.

* **Vloeiende truc**

Deze verbeteringen verbeteren de gebruikerservaring:

・ Aangepaste bitsnelheid en framesnelheid selecteren tijdens het spelen van een truc, op basis van bandbreedte- en bufferprofiel

・ Gebruik de hoofdstream in plaats van de IDR-stream om tot 30 fps snel te kunnen afspelen.

* **Verbeterde ABR-logica**

De nieuwe logica ABR is gebaseerd op bufferlengte, tarief van verandering van bufferlengte, en gemeten bandbreedte. Dit zorgt ervoor dat ABR het juiste beetjetarief kiest wanneer de bandbreedte fluctueert en ook het aantal tijden optimaliseert de bitsnelheidschakelaar eigenlijk door het tarief te controleren waarbij de bufferlengte verandert.

* **Facturering**

TVSDK verzamelt automatisch meetgegevens, met inachtneming van het verkoopcontract van de klant, om periodieke gebruiksrapporten te genereren die voor factureringsdoeleinden worden vereist. Bij elke streamstartgebeurtenis gebruikt TVSDK de API voor het invoegen van Adobe Analytics-gegevens om factuurmetriek, zoals inhoudssoort, voor het invoegen ingeschakelde vlaggen en voor het drm ingeschakelde vlaggen - gebaseerd op de duur van de factureerbare stream - naar de Adobe Analytics Primetime-rapportsuite te verzenden. Dit heeft geen invloed op of wordt niet opgenomen in de eigen Adobe Analytics-rapportreeksen of serveraanroepen van de klant. Op verzoek wordt dit gebruiksrapport voor facturering periodiek naar klanten verzonden. Dit is de eerste fase van de factureringsfunctie die alleen gebruiksfacturering ondersteunt. Het kan worden gevormd gebaseerd op het verkoopcontract gebruikend APIs die in de documentatie worden beschreven.

## Ondersteunde functies {#supported-features}

TVSDK voor Android 2.4 ondersteunt een aantal functies die u kunt implementeren om functionaliteit toe te voegen aan uw videotoepassingen.

>[!NOTE]
>
>In de onderstaande tabel met functiematrix betekent a ð dat de functie wordt ondersteund in de huidige release.

### Core Playback-functies {#core-playback-features}

| **Functie** | **Inhoudstype** | **HLS** | **DASH** |
|---|---|---|---|
| Algemeen afspelen (Afspelen, Pauzeren, Zoeken) | VOD + Live | &amp; | Ö (alleen VOD) |
| FER - Algemeen afspelen (afspelen, pauzeren, zoeken) | FER VOD | &amp; | Niet ondersteund |
| MP3 | VOD | Niet ondersteund | Niet ondersteund |
| MP4-inhoud afspelen | VOD | &amp; | &amp; |
| Adaptive Bit Rate Switching Logic | VOD + Live | &amp; | Niet ondersteund |
| Alleen audio afspelen | VOD + Live | &amp; | Niet ondersteund |
| Ondertiteling - 608/708 | VOD + Live | &amp; | Ö (alleen VOD) |
| Ondertiteling - WebVTT | VOD + Live | &amp; | Ö (alleen VOD) |
| Kennelijke failover | VOD + Live | &amp; | Ö (alleen VOD) |
| Geavanceerde failover | VOD + Live | &amp; | Ö (alleen VOD) |
| QoS- en spelersmeldingen | VOD + Live | &amp; | Ö (alleen VOD) |
| Ondersteuning voor cookie headers | VOD + Live | &amp; | Ö (alleen VOD) |
| Ondersteuning voor aangepaste koppen | VOD + Live | Niet ondersteund | Niet ondersteund |
| Parameters voor bufferbesturing instellen | VOD + Live | &amp; | Ö (alleen VOD) |
| Aangepaste besturingselementen voor bitsnelheid instellen | VOD + Live | &amp; | Ö (alleen VOD) |
| Aangepaste Manifest Tags (HLS) / Gebeurtenisstreams (DASH) | VOD + Live | &amp; | Ö (alleen VOD) |
| Laatste gebonden audio | VOD + Live | &amp; | Ö (alleen VOD) |
| 302 Omleiding | VOD + Live | &amp; | Ö (alleen VOD) |

### Geavanceerde afspeelfuncties {#advanced-playback-features}

<table> 
 <tbody>
  <tr>
   <td><strong>Functie</strong></td> 
   <td><strong>Inhoudstype</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Afspelen met verschuiving</td> 
   <td>Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Alleen audio afspelen</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Steen afspelen </td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Vloeiend afspelen van steen (met ABR)</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>ID3-parsering (HLS) / getimede metagegevens (DASH)</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Blackouts </td> 
   <td>VOD + Live</td> 
   <td>Niet ondersteund</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Direct aan</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Ondersteuning voor discontinue markeertekens (HLS) </li> 
     <li>Meerdere perioden (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>302 Wisselingsgevoeligheid</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Ö (alleen VOD)</td> 
  </tr>
  <tr>
   <td>Miniatuurscrubben (iFrame en JPEG)</td> 
   <td>VOD + Live</td> 
   <td>Niet ondersteund</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Integriteit van stream </td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
 </tbody>
</table>

### Core Ad Insertion-functies (CSAI) {#core-ad-insertion-features-csai}

| **Functie** | **Inhoudstype** | **HLS** | **DASH** |
|---|---|---|---|
| Algemeen afspelen, advertenties ingeschakeld | VOD + Live | &amp; | ð (alleen VOD-rollen) |
| FER-inhoud met ingeschakelde advertenties | VOD | &amp; | Niet ondersteund |
| Standaardgedrag advertentie | VOD + Live | &amp; | ð (alleen VOD-rollen) |
| VAST 2,0/3,0 | VOD + Live | &amp; | ð (alleen VOD-rollen) |
| VMAP 1.0 | VOD + Live | &amp; | ð (alleen VOD-rollen) |
| MP4-advertenties | VOD + Live | Ö uit CRS) | Ö uit CRS, alleen voorrollen) |

### Geavanceerde Ad Insertion-functies (CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>Functie</strong></td> 
   <td><strong>Inhoudstype</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Steen afspelen met advertenties ingeschakeld</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Alleen advertentie </td> 
   <td>VOD</td> 
   <td>Niet ondersteund</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Doelparameters</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>ð (alleen VOD-rollen)</td> 
  </tr>
  <tr>
   <td>Aangepaste parameters</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>ð (alleen VOD-rollen)</td> 
  </tr>
  <tr>
   <td>Aangepast gedrag voor advertentie</td> 
   <td>VOD + Live</td> 
   <td>&amp;</td> 
   <td>ð (alleen VOD-rollen)</td> 
  </tr>
  <tr>
   <td>Aangepaste advertentietags</td> 
   <td>Live</td> 
   <td>&amp; </td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Aangepaste AD-oplossingen</td> 
   <td>VOD + Live</td> 
   <td>&amp; </td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Aangepaste en resolver van vrijloopwiel</td> 
   <td>VOD</td> 
   <td>Niet ondersteund</td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>C3 en vervangen </td> 
   <td>VOD + Live</td> 
   <td>&amp; </td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Lazy advertentie laden</td> 
   <td>VOD</td> 
   <td>&amp; </td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Ondersteuning voor discontinue markeertekens - SSAI (HLS) </li> 
     <li>Meerdere perioden (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>&amp; </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Extra's, banneradvertenties en aanklikbare advertenties</td> 
   <td>VOD + Live</td> 
   <td>&amp; </td> 
   <td>ð (alleen VOD-rollen)</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + Live</td> 
   <td>Ö (JS) </td> 
   <td>ð (alleen VOD-rollen)</td> 
  </tr>
  <tr>
   <td>Vroege advertentie afsluiten</td> 
   <td>Live</td> 
   <td>&amp; </td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>Op regels gebaseerde Creative VOD + Live Prioritization</td> 
   <td>VOD + Live</td> 
   <td>&amp; </td> 
   <td>Niet ondersteund</td> 
  </tr>
  <tr>
   <td>CRS-regels </td> 
   <td>VOD + Live</td> 
   <td>&amp; </td> 
   <td>Niet ondersteund</td> 
  </tr>
 </tbody>
</table>

## Functies voor inhoudsbeveiliging {#content-protection-features}

| **Functie** | **Inhoudstype** | **HLS** | **DASH** |
|---|---|---|---|
| AES-codering | VOD + Live | &amp; | Ö (alleen VOD) |
| Voorbeeld AES-codering | VOD + Live | &amp; |  |
| Vertogende stromen | VOD + Live | &amp; |  |
| DRM | VOD + Live | Alleen Primetime DRM (in de toekomst: Widevine) | Alleen Widevine |
| Extern afspelen (RBOP) | VOD + Live | Alleen Primetime DRM | Niet ondersteund |
| Licentie roteren | VOD + Live | Alleen Primetime DRM | Niet ondersteund |
| Toetsrotatie | VOD + Live | Alleen Primetime DRM | Niet ondersteund |

### Integratiefuncties {#integration-features}

| **Functie** | **Inhoudstype** | **HLS** | **DASH** |
|---|---|---|---|
| Adobe Analytics VHL-integratie | VOD + Live | &amp; | &amp; |
| Facturering | VOD + Live | &amp; | Niet ondersteund |

## Functies niet ondersteund {#features-not-supported}

Deze versie van TVSDK biedt geen ondersteuning voor:

* Zwart van advertenties.
* Trage beweging in truc.
* Zoek en speel met MP4-inhoud.
* Voeg toe met MP4-hoofdinhoud.
* Zoek wanneer een advertentie wordt afgespeeld.
* Afspelen van advertenties met media met alleen audio.

## Bekende problemen en beperkingen {#known-issues-and-limitations}

Deze versie van TVSDK heeft de volgende problemen:

* Apparaatspecifiek (Samsung Galaxy Tab 4) crasht VOD DRM LBA met geluid en klik op advertenties
* Naroladvertentie wordt niet afgespeeld voor een specifieke inhoud.
* Het instellen van het bijschrift Sluiten op CJK-talen werkt niet.
* Video kan automatisch uit de truc-modus komen, zowel tussen VOD als live.
* VHL - de verkeerde hartslagvraag wordt verzonden wanneer wij een inhoud van een compensatie beginnen.
* Wanneer VPAID-advertenties VHL-aanroepen voor hartslag voor gebeurtenis:type:play worden afgespeeld en ontbreken.
* Pre-rol en speelt zelfs wanneer addBreakPolicy SKIP wordt gekozen.
* Nadat u naar de statusspeler Volledig bent gegaan, gaat u terug naar de afspeelstatus met SKIP en BreakPolicy voor Post-roll-advertenties.

Zonder video is er geen viewport-dimensie en zonder viewport-dimensie kunt u geen afbeeldingen voor bijschriften weergeven.

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html).