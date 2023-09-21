---
title: Opmerkingen bij de release TVSDK 2.1 PlayStation 4
description: TVSDK 2.1 voor PlayStation 4 Opmerkingen bij de release beschrijven de ondersteunde functies en de bekende problemen in TVSDK 2.1 PlayStation 4.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Opmerkingen bij de release TVSDK 2.1 PlayStation 4 {#tvsdk-playstation-release-notes}

TVSDK 2.1 voor PlayStation 4 Opmerkingen bij de release beschrijven de ondersteunde functies en de bekende problemen in TVSDK 2.1 PlayStation 4.

## Opgeloste problemen {#resolved-issues}

Hier volgen de opgeloste problemen voor TVSDK 2.1 voor PlayStation 4:

**Versie 2.1.0.638**

* **PTPLAY-10439:**
Toen de insteekmodule VMAP en de koppeling werden verbroken, bleef de speler vast in de voorbereidingsstatus (hij stuurde niet `onComplete` aan zijn bezoeker).

* **PTPLAY-10179:**
  `creativeRepackaging` en `fallbackOnInvalidCreative` waarden zijn nu standaard uitgeschakeld. Ook, wanneer `creativeRepackaging` markering is ingesteld maar geen `creativeRepackaging` het formaat is opgegeven, `onRepackagingComplete` werd net zo vaak opgeroepen als er advertenties waren in de advertentie-onderbreking, waardoor er meerdere keren advertentiepauzes werden gemaakt.

* **Zendesk #10304**: De variabele voor de advertentie aan/uit is niet geïnitialiseerd. We initialiseren nu de variabele van `DataSetEntry's` ctor.

* **PTPLAY-10318:**
Ondersteuning voor de achtergrondmodus is geïntroduceerd.
* **Zendesk # 17409:**
Als u overschakelt naar de truc-afspeelmodus, gaat u weer terug naar de normale afspeelmodus en gaat u weer over naar de truc-afspeelmodus, dan springt de afspeelpositie.
* **PTPLAY-952:**
Na het parseren van XML-bestanden met reacties wordt foutcode 1108 nu gepingeld wanneer er geen advertenties aanwezig zijn.
* **PTPLAY-951:**
Wanneer er geen ad onderbreking na de verwerking van de Auditude is, roept CRS **onPrefetchComplete** die de groupCount vermindert. Omdat er geen pauze is, kan de **groupCount** is 0 en wordt met 1 verlaagd. Eerder **groupCount** was **uint32_t** omdat de waarde is gewijzigd in max. Dit is nu **int32_t**.

**Versie 2.1.0.621**

* **Zendesk #4555**
Onmiddellijk bij Geheugenproblemen fouten bij het laden - `MediaItemLoader` Oplossing voor een crash tijdens het loslaten `mediaitemloader`

* **Zendesk #17223**
2.x CSAI: niet alle URL&#39;s die URL&#39;s bijhouden worden geactiveerd
   * Sommige VAST-advertenties wezen op een inlineadvertentie en ontbraken trackingURL&#39;s.
   * Wanneer een advertentie meerdere impositietags bevat in VAST XML, werd alleen de eerste immateriële URL opgeslagen en de rest genegeerd. Nu worden alle impressie-URL&#39;s later opgeslagen en gepingeld.
* **Zendesk #17224**
PS4-gebruikersagent verplaatst de primetime-informatie naar het einde van de UAString
* **Zendesk #17226**
2.x CSAI: Niet alle advertenties zijn ingeklemd.\
  Met Repareren wordt aangegeven dat de tijdlijn is gewijzigd als gevolg van insertBy- of eraseBy-bewerkingen en wordt de periode dienovereenkomstig aangepast.

* **Zendesk #17284**
  [Alle platforms] Gesloten bijschriften worden niet weergegeven.\
  HLS - steun voor `EXT-X-MEDIA-TIME` -tag voor VTT-bijschriftbestanden.

* **Zendesk #17889**
&quot;Milky&quot; afspelen op PS4\
  correct toegepaste yoffset (voor kleurconversie)

* **Zendesk #17954**
Extra fallback-logica + lege, grote verwerking\
  Probleem verholpen als een van de Vast-wrappers leeg was, werd de Vast-parser gebruikt om de wrapper verder te verwerken.

* **Zendesk #17807**
Kan niet voorbij lege massa zoals Zendesk #3103

* **Zendesk #17865**
Fallback Logic op PS4 en XBox One\
  Hetzelfde als Zendesk #3103

**Versie 2.1.0.591**

* **Zendesk #3767**
PS4 Ad-codefragment. Het oplossen van Ad-problemen mislukt bij het verwerken van VMAP-omleidingen.
* **Zendesk #4096**
PS4 CSAI: segmentatiefout Probleem opgelost als TVSDK een segmentatiefout genereert wanneer een VMAP-reactie wordt verwerkt in de bibliotheek.

* **Zendesk #4161**
Trickplay 16x aan het eind van de film bevriest Vaste impasse die wanneer het trickplay aan normaal playback terugkeert

* **Zendesk #4208**
Willekeurig crashen wanneer Closed Captions is ingeschakeld Vast geheugenlek wanneer Closed Captions is ingeschakeld

* **Zendesk #4213**
PS4 CSAI: Verandering standaarduser-agent koord voor alle op elkaar betrekking hebbende vraag wordt de gebruiker-agent koord gecreeerd gebruikend het zelfde koord van UA dat browser gebruikt + voegt koord Primetime toe

* **PTPLAY-7675** (interne) Getranscodeerde advertenties spelen geen Creative Repackaging uit als deze worden aangeroepen in een VMAP- of VAST-reactie. Als u dit corrigeert, hoeft u alleen maar de mediafile te lezen van advertentie in plaats van te lezen van de asset voor grote advertenties.

* **PTPLAY-7895** (internal) Wanneer `allowMultipleAds=false`, geen advertenties Vaste bug afspelen `allowMultipleAds` parameter niet correct wordt uitgevoerd.

* **PTPLAY-7896** (interne) Advertenties zijn in PS4 in volgorde afgespeeld. Dit probleem is nu opgelost. Advertenties waren namelijk niet in de volgorde waarin de advertenties in de XML-reacties werden weergegeven.

* PS4 TVSDK is opnieuw getest in een mini-app in plaats van in een game.

**Versie 2.1.0.563**

* **Zendesk #3868**
Biedt TVSDK ondersteuning voor Playstation SDK 2.5 De TVSDK is nu gebouwd met de 2.5 Playstation SDK.

* **Zendesk #4093**
het richten van sleutel-waardeparen van Info in Pt Ads verzoek.\
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

* Zie de volledige Help-documentatie op [Adobe Primetime - Meer informatie en ondersteuning](https://experienceleague.adobe.com/docs/primetime.html) pagina.
