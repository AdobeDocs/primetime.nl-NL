---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: Creatieve selectieregels toepassen
title: Creatieve selectieregels toepassen
uuid: 313306b7-6b99-4d90-8717-2b0a1e39a07b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Creatieve selectieregels toepassen{#apply-creative-selection-rules}

TVSDK past creatieve selectieregels op de volgende manieren toe:

* TVSDK past eerst alle `default` regels toe, gevolgd door de zonespecifieke regels.
* TVSDK negeert regels die niet zijn gedefinieerd voor de huidige zone-id.
* Zodra TVSDK de standaardregels toepast, kunnen de zone-specifieke regels de creatieve prioriteiten verder veranderen die op `host` (domein) gelijken op creatief worden gebaseerd die door de `default` regels worden geselecteerd.

* Als TVSDK in het meegeleverde bestand met voorbeeldregels de `default`-regels toepast en het creatieve M3U8-domein [!DNL my.domain.com] of [!DNL a.bcd.com] niet bevat en de advertentieruimte `1234` is, worden de creatieve items opnieuw geordend en wordt de creatieve Flash VPAID afgespeeld als deze beschikbaar is. Anders wordt een MP4-advertentie afgespeeld, enzovoort, tot aan JavaScript.

* Als een advertentie is geselecteerd die TVSDK niet native kan afspelen ( [!DNL .mp4], [!DNL .flv], enz.), geeft TVSDK een aanvraag voor het opnieuw verpakken uit.

Merk op dat de advertentietypes die door TVSDK kunnen worden behandeld nog door `validMimeTypes` het plaatsen in `AuditudeSettings` worden bepaald.
