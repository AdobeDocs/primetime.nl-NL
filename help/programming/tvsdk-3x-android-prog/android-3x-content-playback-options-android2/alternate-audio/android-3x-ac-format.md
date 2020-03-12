---
description: Met de Audio Codec 3 (AC-3, ook bekend als Dolby Digital®) 5.1-indeling kunnen inhoudsproviders de grootte van multikanaalsaudiobestanden comprimeren zonder dat dit de geluidskwaliteit nadelig beïnvloedt. AC-3 is een formaat 5.1, zo betekent het dat het vijf volledig-bandbreedtekanalen voor een rijkere gebruikerservaring verstrekt.
seo-description: Met de Audio Codec 3 (AC-3, ook bekend als Dolby Digital®) 5.1-indeling kunnen inhoudsproviders de grootte van multikanaalsaudiobestanden comprimeren zonder dat dit de geluidskwaliteit nadelig beïnvloedt. AC-3 is een formaat 5.1, zo betekent het dat het vijf volledig-bandbreedtekanalen voor een rijkere gebruikerservaring verstrekt.
seo-title: AC-3 5.1-indeling
title: AC-3 5.1-indeling
uuid: 9d1adf33-4c9b-4d31-8212-ac301f3e44c5
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# AC-3 5.1-indeling {#ac-format}

Met de Audio Codec 3 (AC-3, ook bekend als Dolby Digital®) 5.1-indeling kunnen inhoudsproviders de grootte van multikanaalsaudiobestanden comprimeren zonder dat dit de geluidskwaliteit nadelig beïnvloedt. AC-3 is een formaat 5.1, zo betekent het dat het vijf volledig-bandbreedtekanalen voor een rijkere gebruikerservaring verstrekt.

Zie [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html)voor meer informatie.

TVSDK ondersteunt de volgende AC-3 5.1-functies:

* AC-3 surround audio
* Gemengde/niet-gemengde streams voor surround-audiotypen
* Mogelijkheid om het apparaat te vragen om te controleren of de surround-audiocodec beschikbaar is op het apparaat.

   De resultaten bepalen welk voorkeurstype voor audiocodec is geselecteerd. Het manifest met audiocodetype dat het apparaat niet zal gebruiken wordt verworpen. Als bijvoorbeeld de indeling AC-3 is geselecteerd, worden profielen met de indeling Advanced Audio Coding (AAC) niet in aanmerking genomen.
* Passthrough-modus

   In de passthrough-modus wordt de TVSDK-indeling gewijzigd of ongewijzigd (afhankelijk van het apparaat) Dolby-media van de Decoder in plaats van de media te decoderen van de AC-3 5.1-indeling naar een PCM-indeling (multi-channel pulse-code modululation). Deze media worden naar het audioapparaat (luidspreker of ontvanger) verzonden, zodat het audioapparaat de Dolby-surround-stream kan decoderen en afspelen.

>[!IMPORTANT]
>
>TVSDK biedt alleen ondersteuning voor de AC-3 5.1-functies op het apparaat van de eerste generatie Amazon Fire TV.

De volgende AC-3 5.1-functies worden niet ondersteund:

* AAC-audio met meerdere kanalen
* ABR voor verschillende codecs (AAC - AC3)

## Ondersteunde media selecteren {#section_0D7E717BE18B418D817EE017EF2375D1}

Hier is het typische werkschema dat voorkomt wanneer TVSDK manifest met AC-3 en AAC media vindt:

1. TVSDK vraagt welke codec het apparaat kan ondersteunen.
1. De codec met de hogere kwaliteit wordt geselecteerd.

   Hier volgt de volgorde waarin kwaliteit is geselecteerd:

   1. AC-3
   1. AAC

1. TVSDK negeert profielen met andere audiocodetypen.

>[!TIP]
>
>De toepassing kan geen informatie ophalen over genegeerde profielen.

## De uitvoermodus bepalen {#section_D2AFBF33D3904AC2A7C653A60C3A0CD3}

Als een Android-apparaat tijdens de verwerking van AC-3-media is aangesloten op het luidsprekersysteem, is de beslissing om inhoud af te spelen in de surround-modus of de stereomodus afhankelijk van de configuratie van het apparaat.

|  | **Surround sound** | **Stereoluidspreker** |
|---|---|---|
| Apparaatconfiguratie Dolby ingeschakeld (of automatisch) | Apparaatconfiguratie Dolby ingeschakeld (of automatisch) | Stereomodus |
| Apparaatconfiguratie Dolby uit | Stereomodus | Stereomodus |