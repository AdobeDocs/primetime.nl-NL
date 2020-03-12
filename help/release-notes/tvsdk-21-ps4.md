---
title: Opmerkingen bij de release TVSDK 2.1 PlayStation 4
seo-title: Opmerkingen bij de release TVSDK 2.1 PlayStation 4
description: TVSDK 2.1 voor PlayStation 4 Opmerkingen bij de release beschrijven de ondersteunde functies en de bekende problemen in TVSDK 2.1 PlayStation 4.
seo-description: TVSDK 2.1 voor PlayStation 4 Opmerkingen bij de release beschrijven de ondersteunde functies en de bekende problemen in TVSDK 2.1 PlayStation 4.
uuid: 494569cf-07e2-476a-b88e-e46c9cca4cdc
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: ebfc8819-f5a9-47a2-b454-0e4e6f9e4640
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Opmerkingen bij de release TVSDK 2.1 PlayStation 4 {#tvsdk-playstation-release-notes}

TVSDK 2.1 voor PlayStation 4 Opmerkingen bij de release beschrijven de ondersteunde functies en de bekende problemen in TVSDK 2.1 PlayStation 4.

## Opgeloste problemen {#resolved-issues}

Hier volgen de opgeloste problemen voor TVSDK 2.1 voor PlayStation 4:

**Versie 2.1.0.638**

* **PTPLAY-10439:**
Toen de omslag VMAP en verbinding werd gebroken de speler in het Voorbereiden van staat vastliep (het zond niet `onComplete` naar zijn bezoeker).

* **PTPLAY-10179:**
   `creativeRepackaging` en `fallbackOnInvalidCreative` waarden zijn nu standaard uitgeschakeld. Wanneer de `creativeRepackaging` markering was ingesteld maar geen `creativeRepackaging` indeling was opgegeven, `onRepackagingComplete` werd de markering net zo vaak aangeroepen als er advertenties waren in het ad-einde, waardoor er meerdere keren ad-hocafbrekingen werden gemaakt.

* **Zendesk #10304**:
De variabele advertentievrijheid aan/uit is niet geïnitialiseerd. We initialiseren nu de variabele van `DataSetEntry's` ctor.

* **PTPLAY-10318:**
Ondersteuning voor de achtergrondmodus is geïntroduceerd.
* **Zendesk # 17409:**
Als u overschakelt naar de truc-afspeelmodus, gaat u weer terug naar de normale afspeelmodus en gaat u weer over naar de truc-afspeelmodus, dan springt de afspeelpositie.
* **PTPLAY-9552:**
Na het parseren van XML-bestanden met reacties wordt foutcode 1108 nu gepingeld wanneer er geen advertenties aanwezig zijn.
* **PTPLAY-9551:**
Wanneer er geen ad onderbreking na de verwerking van de Omschrijving is, roept CRS **onPrefetchComplete** die groupCount vermindert. Aangezien er geen ad-break is, is **groupCount** 0 en met 1 verlaagd. Eerder was **groupCount** **uint32_t** , waardoor de waarde werd gewijzigd in max. Dit is nu **int32_t**.

**Versie 2.1.0.621**

* **Zendesk #4555**`MediaItemLoader` Instant on Memory issues leading-Loading errors - Fix for crash occurred while releasing `mediaitemloader`

* **Zendesk #17223** 2.x CSAI: Niet alle URL&#39;s met URL&#39;s die worden bijgehouden, zijn geactiveerd
   * Sommige VAST-advertenties wezen op een inlineadvertentie en ontbraken trackingURL&#39;s.
   * Wanneer een advertentie meerdere impositietags bevat in VAST XML, werd alleen de eerste immateriële URL opgeslagen en de rest genegeerd. Nu worden alle impressie-URL&#39;s later opgeslagen en gepingeld.
* **De gebruikersagent van Zendesk #17224** PS4 verplaatst primetime informatie aan het eind van UAString
* **Zendesk #17226** 2.x CSAI: Niet alle advertenties zijn ingeklemd.\
   Met Repareren wordt aangegeven dat de tijdlijn is gewijzigd als gevolg van insertBy- of eraseBy-bewerkingen en wordt de periode dienovereenkomstig aangepast.

* **Zendesk #17284**
   [Niet alle platformen] met ondertitels worden weergegeven.\
   HLS - ondersteuning voor de `EXT-X-MEDIA-TIME` tag voor VTT-bijschriftbestanden.

* **Zendesk #17889** Playback &quot;Milky&quot; op PS4\
   correct toegepaste yoffset (voor kleurconversie)

* **Zendesk #17954** Ad fallback logic + verwerking van lege, grote\
   Probleem verholpen als een van de Vast-wrappers leeg was, werd de Vast-parser gebruikt om de wrapper verder te verwerken.

* **Zendesk #17807** Kan lege maapHetzelfde als Zendesk niet voorbij krijgen #3103

* **Zendesk #17865** Fallback Logic op PS4 en XBox One\
   Hetzelfde als Zendesk #3103

**Versie 2.1.0.591**

* **Het codefragment Zendesk #3767** PS4 Ad, en het oplossen van problemen van de Oplossing ontbreekt wanneer het verwerken van VMAP omleidt.
* **Zendesk #4096** PS4 CSAI: SegmentatiefoutFixed crasht wanneer TVSDK een segmentatiefout genereert wanneer de advertentiebibliotheek een VMAP-reactie verwerkt.

* **Zendesk #4161** Trickplay 16x aan het eind van de film bevriestFixed implock die plaatsvindt wanneer het trickplay aan normale playback terugkeert

* **Zendesk #4208** Willekeurig crashen als Closed Captions zijn ingeschakeldHerstel geheugenlek als Closed Captions was ingeschakeld

* **Zendesk #4213** PS4 CSAI: De standaardgebruiker-agentenkoord van de verandering voor al op elkaar betrekking hebbende vraagUser-agent koord wordt gecreeerd gebruikend het zelfde koord van UA dat browser gebruikt + voegt Primetime koord toe

* **PTPLAY-7675** (internal)Getranscodeerde advertenties spelen nietCreative Repackaging faalde toen het binnen een reactie VMAP of VAST aanriep. Als u dit corrigeert, hoeft u alleen maar de mediafile te lezen van advertentie in plaats van te lezen van de asset in het geval van grote advertenties.

* **PTPLAY-7895** (internal)When `allowMultipleAds=false`, no ads playFixed bug where `allowMultipleAds` parameter was not be followed correctly.

* **PTPLAY-7896** (internal)advertenties spelen op PS4Fixed af in volgorde waarin advertenties niet in de volgorde stonden waarin de advertenties in de XML-reacties werden weergegeven.

* PS4 TVSDK is opnieuw getest in een mini-app in plaats van in een game.

**Versie 2.1.0.563**

* **Zendesk #3868** Does TVSDK support Playstation SDK 2.5The TVSDK is now built with the 2.5 Playstation SDK.

* **Zendesk #4093** targetingInfo sleutel-waardeparen in Pt Ads request.\
   Er is een nieuwe-regelteken toegevoegd dat de sleutel-/waardeparen scheidt.

## Ondersteunde functies {#supported-features}

De volgende functies worden ondersteund in TVSDK 2.1 voor PlayStation 4:

**Versie 2.1.0.621**

* Ad Fallback, Daisy chaining in ad selection logic (Zendesk #3103) For VAST ads (creatives) with the fallback rule enabled, the TVSDK behandelt een advertentie met een ongeldig MIME type als een lege advertentie en probeert fallback advertenties in zijn plaats te gebruiken.U kunt enkele aspecten van fallback-gedrag configureren

**Versie 2.1.0.538**

* HLS VOD afspelen, inclusief afspelen, pauzeren, zoeken
* Adaptieve streaming bitsnelheid
* Gecodeerde inhoud afspelen met door Primetime DRM en vanilla AES beveiligde inhoud
* Client-kant en invoeging met standaard- en advertentiefuncties en advertentievrijheid
* Creatief opnieuw verpakken
* WebVTT-ondertiteling
* Inschakelen met aangepaste startpositie
* Stekelspel met snel vooruit en snel terugspoelen
* 302 omleiding

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html) .