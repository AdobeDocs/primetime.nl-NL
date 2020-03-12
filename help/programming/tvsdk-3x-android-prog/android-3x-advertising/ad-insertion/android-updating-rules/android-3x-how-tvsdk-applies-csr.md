---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: Creatieve selectieregels toepassen
title: Creatieve selectieregels toepassen
uuid: 66e55f95-25ce-4838-b222-63ee34e535d1
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Creatieve selectieregels toepassen {#apply-creative-selection-rules}

TVSDK past creatieve selectieregels op de volgende manieren toe:

* TVSDK past eerst alle `default` regels toe, gevolgd door de zonespecifieke regels.
* TVSDK negeert regels die niet zijn gedefinieerd voor de huidige zone-id.
* Zodra TVSDK de standaardregels toepast, kunnen de zone-specifieke regels de creatieve prioriteiten verder veranderen die op de (domein) gelijken op creatief worden gebaseerd die door de `host` `default` regels worden geselecteerd.

* Als TVSDK de `default` regels toepast en het creatieve domein van de M3U8 geen of `my.domain.com` `a.bcd.com` `1234`en de advertentieruimte is, worden de creatieve items opnieuw gerangschikt en wordt de creatieve Flash VPAID-speler afgespeeld als deze beschikbaar is in het bestand met voorbeeldregels met aanvullende zoneregels. Anders wordt een MP4-advertentie afgespeeld, enzovoort, tot aan JavaScript.

* Als u een creatieve advertentie selecteert die TVSDK niet native kan afspelen ( [!DNL .mp4], [!DNL .flv]enz.), geeft TVSDK een aanvraag voor het opnieuw verpakken uit.

Merk op dat de advertentietypes die door TVSDK kunnen worden behandeld nog door het plaatsen binnen `validMimeTypes` `AuditudeSettings`worden bepaald.

<!-- 

In Android 2.5 API docs, I see a 
<span class="codeph"> setValidMimeTypes</span> but not a 
<span class="codeph"> getValidMimeTypes</span>.

 -->

