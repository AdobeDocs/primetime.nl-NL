---
description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.
title: AC-3 5.1-indeling
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# AC-3 5.1-indeling{#ac-format}

Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.

Primetime kan niet tegen dergelijke mislukkingen zoals een ISP stroomonderbreking of een kabelontbinding beschermen. Primetime streaming biedt echter bescherming bij uitvalbeveiliging om het afspelen te beschermen tegen bepaalde fouten op de externe server of operationele fouten, waardoor viewers een betere ervaring krijgen. TVSDK implementeert failover-beveiliging om afspeelonderbrekingen tot een minimum te beperken en een naadloze weergave te bereiken ondanks transmissieproblemen. De videospeler schakelt automatisch over naar een back-upmediaset wanneer volledige uitvoeringen of fragmenten niet beschikbaar zijn.

Met de Audio Codec 3 (AC-3, ook bekend als Dolby Digital®) 5.1-indeling kunnen inhoudsproviders de grootte van multikanaalsaudiobestanden comprimeren zonder dat dit de geluidskwaliteit nadelig beïnvloedt. AC-3 is een formaat 5.1, zo betekent het dat het vijf volledig-bandbreedtekanalen voor een rijkere gebruikerservaring verstrekt.

Zie voor meer informatie [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

>[!IMPORTANT]
>
>TVSDK versie 1.4 biedt alleen ondersteuning voor de indeling AC-3 5.1 op Amazon FireTV.

TVSDK ondersteunt de volgende AC-3 5.1-functies:

* AC-3 surround audio
* Gemengde/niet-gemengde streams voor surround-audiotypen
* Mogelijkheid om het apparaat te vragen om te controleren of de surround-audiocodec beschikbaar is op het apparaat.

  De resultaten bepalen welk voorkeurstype voor audiocodec is geselecteerd. Het manifest met audiocodetype dat het apparaat niet zal gebruiken wordt verworpen. Als bijvoorbeeld de indeling AC-3 is geselecteerd, worden profielen met de indeling Advanced Audio Coding (AAC) niet in aanmerking genomen.
* Passthrough-modus

  In de passthrough-modus wordt de TVSDK-indeling gewijzigd of ongewijzigd (afhankelijk van het apparaat) Dolby-media van de Decoder in plaats van de media te decoderen van de AC-3 5.1-indeling naar een PCM-indeling (multi-channel pulse-code modululation). Deze media worden naar het audioapparaat (luidspreker of ontvanger) verzonden, zodat het audioapparaat de Dolby-surround-stream kan decoderen en afspelen.

TVSDK ondersteunt de AC-3 5.1-functies alleen op het Amazon Fire TV-apparaat van de eerste generatie.

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

|   | Surround sound | Stereoluidspreker |
|---|---|---|
| Apparaatconfiguratie Dolby ingeschakeld (of automatisch) | Apparaatconfiguratie Dolby ingeschakeld (of automatisch) | Stereomodus |
| Apparaatconfiguratie Dolby uit | Stereomodus | Stereomodus |
