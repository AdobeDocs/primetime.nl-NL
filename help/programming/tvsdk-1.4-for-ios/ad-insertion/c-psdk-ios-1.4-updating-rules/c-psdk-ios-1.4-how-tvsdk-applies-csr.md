---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: Creatieve selectieregels toepassen
title: Creatieve selectieregels toepassen
uuid: 313306b7-6b99-4d90-8717-2b0a1e39a07b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Creatieve selectieregels toepassen{#apply-creative-selection-rules}

TVSDK past creatieve selectieregels op de volgende manieren toe:

* TVSDK past eerst alle `default` regels toe, gevolgd door de zonespecifieke regels.
* TVSDK negeert regels die niet zijn gedefinieerd voor de huidige zone-id.
* Zodra TVSDK de standaardregels toepast, kunnen de zone-specifieke regels de creatieve prioriteiten verder veranderen die op de (domein) gelijken op creatief worden gebaseerd die door de `host` `default` regels worden geselecteerd.

* Als TVSDK de `default` regels toepast en het creatieve domein van de M3U8 geen of [!DNL my.domain.com] [!DNL a.bcd.com] `1234`en de advertentieruimte is, worden de creatieve items opnieuw gerangschikt en wordt de creatieve Flash VPAID-speler afgespeeld als deze beschikbaar is in het bestand met voorbeeldregels met aanvullende zoneregels. Anders wordt een MP4-advertentie afgespeeld, enzovoort, tot aan JavaScript.

* Als u een creatieve advertentie selecteert die TVSDK niet native kan afspelen ( [!DNL .mp4], [!DNL .flv]enz.), geeft TVSDK een aanvraag voor het opnieuw verpakken uit.

Merk op dat de advertentietypes die door TVSDK kunnen worden behandeld nog door het plaatsen binnen `validMimeTypes` `AuditudeSettings`worden bepaald.
