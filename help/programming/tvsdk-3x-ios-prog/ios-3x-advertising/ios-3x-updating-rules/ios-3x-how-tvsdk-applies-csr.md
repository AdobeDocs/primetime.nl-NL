---
keywords: creatieve selectieregels;AdobeTVSDKConfig
title: Creatieve selectieregels toepassen
description: Creatieve selectieregels toepassen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Creatieve selectieregels toepassen {#apply-creative-selection-rules}

TVSDK past creatieve selectieregels op de volgende manieren toe:

* TVSDK past alle `default` eerst, gevolgd door de zonespecifieke regels.
* TVSDK negeert regels die niet zijn gedefinieerd voor de huidige zone-id.
* Zodra TVSDK de standaardregels toepast, kunnen de zonespecifieke regels de creatieve prioriteiten verder veranderen die op `host` (domein) vindt u op de door de `default` regels.

* Als TVSDK de instelling `default` regels, als het creatieve domein van de M3U8 geen [!DNL my.domain.com] of [!DNL a.bcd.com] en de ad-zone `1234`De creatieve Flash VPAID wordt eerst afgespeeld als deze beschikbaar is. Anders wordt een MP4-advertentie afgespeeld, enzovoort, tot aan JavaScript.

* Als een advertentie is geselecteerd, kan TVSDK niet native worden afgespeeld ( [!DNL .mp4], [!DNL .flv], enz.) geeft TVSDK een aanvraag tot herverpakking uit.

Merk op dat de advertentietypes die door TVSDK kunnen worden behandeld nog door `validMimeTypes` instellen in `AuditudeSettings`.
