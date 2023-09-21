---
title: Opmerkingen bij de release PTAI 19.11.1
description: In de release van PTAI 19.11.1 wordt beschreven wat nieuw of gewijzigd is, wat de opgeloste en bekende problemen zijn in Primetime Ad Insertion in 2019.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1971'
ht-degree: 0%

---

# Opmerkingen bij de release van Primetime Ad Insertion 19.11.1

Opmerkingen bij de release van Primetime Ad Insertion 19.11.1 beschrijven nieuwe of gewijzigde, opgeloste problemen en bekende problemen in Primetime Ad Insertion in 2019.

## Nieuw in PTAI 19.11.1

**Wanneer:** Maandag 4 november 2019 om 12.01 uur tot 13.00 uur OOSTEN

Onderhoudsupdates.

## Wat veranderde in vorige versies

### Versie 19.10.2

**Wanneer:** Donderdag 31 oktober 2019, 13.00 tot 3.00 uur Oost

Onderhoudsupdates.

### Versie 19.10.1

**Wanneer:**  Dinsdag 22 oktober om 13.00 uur tot 20.00 uur OOSTENRIJK

Onderhoudsupdates.

### Versie 19.9.1

**Wanneer:** Dinsdag 10 september 2019, 12.30 uur tot 2.00 uur Oosterse tijd

Beveiligingsupdates

### Versie 19.8.3

**Wanneer:** Woensdag 28 augustus 2019, 12:30 - 13:30 uur OOSTENRIJK

Oplossing voor een bug waarbij Chromecast-spelers het afspelen onverwachts beëindigden wanneer ad-segmenten uit het DVR-venster werden gerold.

### Versie 19.8.2

**Wanneer:** Woensdag 21 augustus 2019, 2:00 tot 3:00 uur Oosterse tijd

* SSAI-dashboard: sectie Sessiestaten. U kunt de sessiegebeurtenissen exporteren via de optie CSV downloaden.

* Onderhoudsupdates

### Versie 19.8.1

**Wanneer:** Dinsdag 6 augustus 2019 2:30 uur &#39;s morgens om 19.00 uur tot dinsdag 6 augustus 2019 4:30 uur &#39;s morgens om 19.00 uur

* SSAI-dashboard: nieuwe sectie, Sessiestatistieken, toegevoegd aan het SSAI-dashboard
   * Als u Sessie-id hebt voor een SSAI-sessie waarvoor de foutopsporingsmodus is ingeschakeld (ptdebug=true), kunt u de volgende activiteit die zich tijdens die sessie heeft voorgedaan, opzoeken:
      * Aanvragen/antwoorden toevoegen
      * Ingevoegde advertenties
      * Afgegaan bakens (alleen voor reeksspatiëring op de server)

   * U kunt tot 30 dagen na die SSAI-sessie activiteit opzoeken voor een specifieke sessie-id
   * U kunt de gebeurtenissen exporteren
* Database: beveiligingsupdates

### Versie 19.7.1

**Wanneer:** Woensdag 10 juli

* SSAI: Voor ptcueformat-waarden die EXT-X-CUE-OUT en break het signaleren in levende stromen steunen, voegde een generische macro toe om gegevens van attributen in het EXT-X-ASSET markeringsvoorbeeld over te gaan: Markering die bij de #EXT-X-CUE-OUT markering: #EXT-X-ASSET:CAID=75BCD15, GENRE=News,Program NewsAt10 Macro&#39;s: # kan worden gebruikt om Nieuws (van het attribuut GENRE) tot een ad call URL # over te gaan kan worden gebruikt om NewsAt10 (van het attribuut van het Programma) tot een ad call URL Uitzondering over te gaan: Voor achterwaartse verenigbaarheid, # en # hebben de zelfde functionaliteit. Beide macro&#39;s kunnen worden gebruikt om de waarde van het attribuut CAID door te geven, na het omzetten van de waarde van hexadecimale in lange. De lange waarde is 123456789 voor de hexadecimale waarde, 75BCD15, in het bovenstaande voorbeeld. Beide macro&#39;s worden gebruikt om 123456789 door te geven aan een URL voor een advertentieaanroep. De macro begint altijd met #. De macro is hoofdlettergevoelig, maar het kenmerk in de tag EXT-X-ASSET is dat niet. Dat wil zeggen dat zowel PROGRAMMA als Programma zijn toegestaan in de EXT-X-ASSET-tag
* SSAI: De veranderingen van de configuratie voor een specifieke klant voor het volgende:
   * Een vensterlengte (live afspeellijst) van vier minuten
   * Als een uitzondering van de contactdoosonderbreking wordt geworpen wanneer de Manifest Server broninhoud haalt, zal de Manifest Server de antwoordcode van HTTP (404) in plaats van 500 terugkeren
* Beveiligingsupdates

### Versie 19.6.1

**Wanneer:** Woensdag 12 juni 2019 11:30 PM PST tot donderdag 13 juni 2019 12:30 PST

* CRS: Normalisatieregel voor creatieve personen uit RevJet
   * Toegevoegde regel voor creatieve URL-normalisatie voor RevJet, gebruikt door CRS en SSAI
   * TVSDK: Als u advertenties van RevJet aanbiedt of van plan bent te bedienen, moeten normalisatieregels worden toegevoegd aan de CRS Rules JSON om CRS met hun creatieven te kunnen gebruiken. Neem contact op met uw technische accountmanager voor hulp
* CRS: Normalisatieregel voor creatieve producten van Innovid
   * Toegevoegde creatieve URL-normalisatieregel voor Innovid, gebruikt door SSAI
   * De normalisatieregel die door CRS wordt gebruikt werd toegevoegd in een vroegere versie
   * TVSDK: De normalisatieregel die in de CRS-regels JSON moet worden toegevoegd, is na een eerdere release beschikbaar, maar om veilig te zijn, kunt u contact opnemen met uw technische accountmanager om alle normalisatieregels die u hebt, te controleren.
     >[!NOTE]
     >
     >De meeste innovatieve creatieve URL&#39;s worden getranscodeerd en zonder de normalisatieregel vastgezet. Soms worden echter innovatieve creatieve URL&#39;s met dynamische parameters aangetroffen. De normalisatieregel is nodig om deze instanties te behandelen.

### Versie 19.5.2

**Wanneer:** Woensdag 22 mei 20:30 Oosterse tijd tot woensdag 22 mei 2011 4:30 Oosterse tijd

* Toegevoegde ondersteuning voor CMAF (HLS/fMP4-inhoud)
   * SSAI: CMAF-manifests verwerken
   * SSAI: Initieer transcoderingsverzoeken en haal CRS-middelen op, afhankelijk van de inhoudsindeling (HLS/ts en HLS/fMP4)
   * CRS: toegevoegde workflow om advertenties te herverpakken naar de CMAF-indeling (HLS/fMP4)
* SSAI: Probleem verholpen waarbij niet-gedempte advertenties niet konden worden ingevoegd in ongedempte inhoud, wanneer zowel de inhoud als de advertentie geen audio-alleen stromen hebben (EXT-X-STREAM-INF)
* SSAI: Toegevoegde ondersteuning voor CDN-auth-tokens (Limelight, LLNW) voor inhoudssegmenten
   * Wanneer `pttoken=limelight` of `pttoken=llnw` wordt toegevoegd aan de laarzentrekker URL, zullen wij een geheime kopbal toevoegen wanneer het terugwinnen van de bron master playlist, dan zullen wij de vraagparameters van X-Adobe-Sig van LLNW kopbal aan de inhoudssegmenten toevoegen
* SSAI: nog een token-waarde toegevoegd (`pttoken=centurylink`) voor CDN-ondersteuning voor auteur-token van CenturyLink, uitgebracht op 30 juli 2018
   * `pttoken=centurylink` heeft hetzelfde gedrag als `pttoken=level3`en beide waarden zijn geldig

### Versie 19.5.1

**Wanneer:** Donderdag 9 mei 2010 - 00:30 - 18:30 uur Oosterse tijd

* SSAI: Beveiligingsupdates
* CRS-dashboard: de tekenreeks &quot;FqAdId Sample&quot; is afgevlakt tot 255 tekens vanwege gegevensopslagbeperkingen (8 bits)
   * De tekenreeks FqAdId Sample bevat het Advertentiesysteem en de Advertentie-id van elke XML-reactie in de wrapperketen van de advertentie voor invoegingen van alle CRS-advertenties met SSAI (sectie Creative Stats van het CRS-dashboard)
* SSAI- en CRS-dashboards: updates van softwareversies

### Versie 19.4.1

**Wanneer:** Woensdag 10 april 2010 - 12:30 uur Oosterse tijd tot woensdag 10 april 19:30 uur Oosterse tijd

* CRS: De API voor het opnieuw verpakken van CRS biedt geen ondersteuning meer voor HTTP POST-opdrachten. De API voor opnieuw verpakken van CRS leidt (301) HTTP-POST-opdrachten automatisch om naar HTTPS
   * Vanaf 20 mei wordt HTTP->HTTPS-omleiding voor HTTP POST-opdrachten uitgeschakeld
   * Als u de API voor het opnieuw verpakken van CRS gebruikt om advertenties vooraf te verpakken, gelieve uw bevelen van de POST aan HTTPS tegen 20 Mei te schakelen
* CRS: Opnieuw ontworpen de architectuur en het werkschema voor het uploaden van de activa van CRS aan klanten&#39; CDN oorsprong
   * Taakprocessen per CDN-oorsprong worden gescheiden, dus uploadknelpunten voor één CDN-oorsprong hebben geen invloed op uploads naar andere CDN-oorsprong.
   * Andere voordelen: CRS de baanverwerkingstijden en uploadsnelheden aan klanten&#39; CDN-oorsprong worden verbeterd
* SSAI: Toegevoegde ClickThrough en ClickTracking URLs voor videoadvertenties aan sidecar JSON v2 formaat
   * Een nieuwe JSON-array-eigenschap, &#39;videoClicks&#39;, volgt de eigenschap &#39;trackingURLs&#39;
   * De namen van de waarde &quot;event&quot; zijn &quot;clickThrough&quot; en &quot;clickTracking&quot; en hebben geen begintijdwaarde
* SSAI: Voor CRS-middelen, toegevoegde functionaliteit om de vervaldatum van het opzoekverslag van een CRS-middel met 30 dagen uit te breiden wanneer het wordt opgenomen
   * Vorig gedrag: records voor opzoeken van CRS-middelen worden in elke pod opgeslagen in het geheugen. Opzoekrecords voor CRS-middelen worden 30 dagen na het toevoegen aan het geheugen automatisch verwijderd. Als u de opzoekrecord van een creatief CRS-element wilt herhalen in een pod nadat deze uit het geheugen is verwijderd, moet u driemaal op dat creatieve element in die pod terugkeren
   * Nieuw gedrag: wanneer een pod toegang krijgt tot een opzoekrecord met CRS-middelen om het CRS-element in te voegen, wordt de vervaldatum van de opzoekrecord van het CRS-element in die pod met 30 dagen verlengd. Als gevolg hiervan worden vaak gebruikte CRS-elementen pas 30 dagen nadat deze voor het laatst zijn gebruikt uit de geheugencache van een pod verwijderd
   * Het nieuwe gedrag is systeembreed en kan worden uitgeschakeld als een prestatieverlies wordt gedetecteerd
* SSAI: Bijgewerkt WebVTT manifest-manipulatie gedrag voor levende stromen slechts
   * Vorig gedrag: In manifest WebVTT slechts, verwijder markeringen EXT-X-DISCONTINUITY die vóór elke opgenomen en na het laatste segment van opgenomen en onderbreking zouden worden opgenomen
   * Nieuw gedrag: een nieuwe parameter, vttdisc, met geaccepteerde waarden true en false, toegevoegd aan de SSAI bootstrap URL
      * vttdisc=true: EXT-X-DISCONTINUITY-tags worden ingevoegd in het WebVTT-manifest vóór elke ingevoegde en na het laatste segment van de ingevoegde en-onderbreking, overeenkomstig het gedrag voor audio/video- en alleen-audio manifests
      * vttdisc=false (zelfde als vorig gedrag): In manifest WebVTT slechts, verwijder markeringen EXT-X-DISCONTINUITY die vóór elke opgenomen en na het laatste segment van opgenomen en onderbreking zouden worden opgenomen
      * Als de vttdisc-parameter wordt weggelaten of een andere waarde dan true/false heeft, wordt vttdisc standaard ingesteld op true
* SSAI: beveiligingsupdates en updates van softwareversies
   * Java: Bijgewerkte Java-versie voor ondersteuning van extra cdersuites voor ad-hocoproepen die worden gestart via TLS 1.2 (HTTPS)

### Versie 19.2.1

**Wanneer:** Woensdag 20 februari 2019 13:30 uur Oosterse tijd tot woensdag 20 februari 2019 3:30 uur Oosterse tijd

* SSAI: Toegevoegde ClickThrough en ClickTracking URLs voor videoadvertenties aan sidecar JSON v2 formaat
   * Onder de eigenschap &quot;trackingURLs&quot; zijn de namen van de waarde &#39;event&#39; &#39;clickthrough&#39; en &#39;clickTracking&#39;
   * Hun begintijd-waarden zullen het begin van de advertentie zijn
* SSAI: Voor CRS-middelen, toegevoegde functionaliteit om de vervaldatum van het opzoekverslag van een CRS-middel met 30 dagen uit te breiden wanneer het wordt opgenomen
   * Vorig gedrag: records voor opzoeken van CRS-middelen worden in elke pod opgeslagen in het geheugen. Opzoekrecords voor CRS-middelen worden 30 dagen na het toevoegen aan het geheugen automatisch verwijderd. Als u de opzoekrecord van een creatief CRS-element wilt herhalen in een pod nadat deze uit het geheugen is verwijderd, moet u driemaal op dat creatieve element in die pod terugkeren
   * Nieuw gedrag: wanneer een pod toegang krijgt tot een opzoekrecord met CRS-middelen om het CRS-element in te voegen, wordt de vervaldatum van de opzoekrecord van het CRS-element in die pod met 30 dagen verlengd. Als gevolg hiervan worden vaak gebruikte CRS-elementen pas 30 dagen nadat deze voor het laatst zijn gebruikt uit de geheugencache van een pod verwijderd
   * Het nieuwe gedrag is systeembreed en kan worden uitgeschakeld als een prestatieverlies wordt gedetecteerd

* SSAI: Software-versie-updates voor NGINX en Kafka
   * NGINX en Kafka worden gebruikt voor het branden en volgen van URL&#39;s op de server en het doorsturen van gegevens naar de SSAI- en CRS-dashboards
* CRS: Prestatieverbeteringen op het CRS-dashboard

### Web UI-release

**Wanneer:** Woensdag 13 februari, 4:00 - 4:30 Pacific

**Wat:** UI-component Primetime en besluitvorming

* Probleem met de gebruikersinterface van de kalender verhelpen waarbij de gebruiker geen datum na 31 december 2018 kan selecteren uit de agendacomponent tijdens het verhandelen van een campagne of het trekken van een rapport.

### Versie 19.1.2

**Wanneer:** Woensdag 30 januari 2019 13:30 uur Oosterse tijd tot woensdag 30 januari 3:30 uur Oosterse tijd

* SSAI: Bijgewerkt de raadpleging-zeer belangrijke structuur die SSAI gebruikt om activa van CRS op te slaan en terug te winnen, om scenario&#39;s te behandelen waar de leveranciers van advertenties dynamische identiteitskaart of Creative identiteitskaart voor de zelfde advertentie hebben
   * Nieuwe lookup-key-structuur: Zone, Creative URL en opmaakparameters (doelduur, uitvoerindeling, doel-CDN)
   * Oude lookup-key-structuur: Zone, Ad System, Ad ID, Creative ID, Creative URL en opmaakparameters (doelduur, uitvoerindeling, doel-CDN)
   * De opzoeksleutels voor bestaande CRS-elementen worden bijgewerkt zodat deze overeenkomen met de nieuwe structuur vóór de productievrijgave. Houd er echter rekening mee dat nieuwe elementen die tussen de opzoeksleutels zijn getranscodeerd, niet kunnen worden gebruikt. Als zo, zouden zij een nieuw CRS verzoek in werking stellen de volgende tijd zij na de versie worden ontmoet

* CRS: de mogelijkheid toegevoegd om CRS-aanvragen van specifieke advertentiesystemen, id&#39;s, creatieve id&#39;s, creatieve URL&#39;s en/of creatieve indelingen te lijsten van gewezen personen/lijsten van gewenste personen

  >Opmerking
  >
  >Adobe voegt regels voor lijsten van gewezen personen toe wanneer advertenties met dynamische waarden (bijvoorbeeld een dynamische parameter in URL) voor dezelfde advertentie worden gevonden. Dergelijke lijst van gewezen personen regels zullen worden onbruikbaar gemaakt nadat de dynamische component, of door de leverancier of door een normalisatieregel wordt opgelost.

   * Als u een lijst van gewezen personen of lijst van gewenste personen regel voor uw streek wilt toevoegen, gelieve uw Technische Manager van de Rekening voor hulp te spreken.

### Versie 19.1.1

**Wanneer:** Woensdag 9 januari 2019 13:30 uur Oosterse tijd tot woensdag 9 januari 3:30 uur Oosterse tijd

* Probleem verholpen waarbij een onjuiste interpretatie van HTTP-headers die in leven blijven, kan leiden tot een fout bij het valideren van binnenkomende creatieve elementen die worden gehost op total-stream.net.
* Probleem verholpen waarbij enkele aanhalingstekens (&#39;) en dubbele aanhalingstekens (&#39;) in advertentie-id, Creative ID en andere velden voor een herverpakkingsaanvraag ertoe leidden dat de herverpakkingsaanvraag mislukte.
* Overgeschakeld naar Java long (gegevenstype) om een probleem aan te pakken waarbij het bereiken van de Java int-limiet van 2.147.483.647 in de waarden van de transcoderings-taak ertoe zou leiden dat alle herverpakkingsverzoeken mislukken.
* Databasoptimalisaties.

## Opgeloste problemen

Wanneer de oplossing aan een gemelde kwestie wordt geassocieerd, wordt een verwijzing van Zendesk getoond. Bijvoorbeeld ZD#xxxxx.

**PTAI 19.7.1**

ZD#37503 - JSON-reacties voor de CRS-regels worden in cache geplaatst om dubbele aanvragen te voorkomen.

## Bekende problemen en beperkingen

**PTAI 19.7.1**

Geen nieuwe beperking toegevoegd.
