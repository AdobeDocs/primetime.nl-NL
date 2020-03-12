---
description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat extern afspelen mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.
seo-description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat extern afspelen mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.
seo-title: AC-3 5.1-indeling
title: AC-3 5.1-indeling
uuid: d5e77bb5-ed51-4f9f-b34f-e9082f5ee4de
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# AC-3 5.1-indeling{#ac-format}

Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat extern afspelen mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.

Primetime kan niet tegen dergelijke mislukkingen zoals een ISP stroomonderbreking of een kabelontbinding beschermen. Primetime streaming biedt echter bescherming bij uitvalbeveiliging om het afspelen te beschermen tegen bepaalde fouten op de externe server of operationele fouten, waardoor viewers een betere ervaring krijgen. TVSDK implementeert failover-beveiliging om afspeelonderbrekingen tot een minimum te beperken en een naadloze weergave te bereiken ondanks transmissieproblemen. De videospeler schakelt automatisch over naar een back-upmediaset wanneer volledige uitvoeringen of fragmenten niet beschikbaar zijn.

Met de Audio Codec 3 (AC-3, ook bekend als Dolby Digital®) 5.1-indeling kunnen inhoudsproviders de grootte van multikanaalsaudiobestanden comprimeren zonder dat dit de geluidskwaliteit nadelig beïnvloedt. AC-3 is een formaat 5.1, zo betekent het dat het vijf volledig-bandbreedtekanalen voor een rijkere gebruikerservaring verstrekt.

Zie [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html)voor meer informatie.

>[!IMPORTANT]
>
>TVSDK versie 1.4 ondersteunt de indeling AC-3 5.1 alleen op Amazon FireTV.

TVSDK ondersteunt de volgende AC-3 5.1-functies:

* AC-3 surround audio
* Gemengde/niet-gemengde streams voor surround-audiotypen
* Mogelijkheid om het apparaat te vragen om te controleren of de surround-audiocodec beschikbaar is op het apparaat.

   De resultaten bepalen welk voorkeurstype voor audiocodec is geselecteerd. Het manifest met audiocodetype dat het apparaat niet zal gebruiken wordt verworpen. Als bijvoorbeeld de indeling AC-3 is geselecteerd, worden profielen met de indeling Advanced Audio Coding (AAC) niet in aanmerking genomen.
* Passthrough-modus

   In de passthrough-modus wordt de TVSDK-indeling gewijzigd of ongewijzigd (afhankelijk van het apparaat) Dolby-media van de Decoder in plaats van de media te decoderen van de AC-3 5.1-indeling naar een PCM-indeling (multi-channel pulse-code modululation). Deze media worden naar het audioapparaat (luidspreker of ontvanger) verzonden, zodat het audioapparaat de Dolby-surround-stream kan decoderen en afspelen.

TVSDK biedt alleen ondersteuning voor de AC-3 5.1-functies op het apparaat van de eerste generatie Amazon Fire TV.

De volgende AC-3 5.1-functies worden niet ondersteund:

* AAC-audio met meerdere kanalen
* ABR voor verschillende codecs (AAC - AC3)

## Ondersteunde media selecteren {#section_E1DFA1F472EA4BDE846C71A3343E275A}

Hier is het typische werkschema dat voorkomt wanneer TVSDK manifest met AC-3 en AAC media vindt:

1. TVSDK vraagt welke codec het apparaat kan ondersteunen.
1. De codec met de hogere kwaliteit wordt geselecteerd.

   De kwaliteitsvolgorde is AC-3 > AAC.
1. TVSDK negeert profielen met andere audiocodetypen.

>[!TIP]
>
>De toepassing kan geen informatie ophalen over genegeerde profielen.

## De uitvoermodus bepalen {#section_64145D9824594C36AADBF0482C528767}

Als een Android-apparaat tijdens de verwerking van AC-3-media is aangesloten op het luidsprekersysteem, is de beslissing om inhoud af te spelen in de surround-modus of de stereomodus afhankelijk van de configuratie van het apparaat.

|  | Surround sound | Stereoluidspreker |
|---|---|---|
| Apparaatconfiguratie Dolby ingeschakeld (of automatisch) | Apparaatconfiguratie Dolby ingeschakeld (of automatisch) | Stereomodus |
| Apparaatconfiguratie Dolby uit | Stereomodus | Stereomodus |

