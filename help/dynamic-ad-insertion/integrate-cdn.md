---
title: Uw CDN integreren
description: De CDN integreren
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# De CDN {#integrating-cdn} integreren

Primetime Ad Insertion fungeert als een proxy tussen uw clienttoepassing en manifests, niet de videoblokken zelf. Implementeer uw inhoud naar de CDN van uw keuze en geef de URL door aan Primetime Ad Insertion met behulp van de Bootstrap-API.<!-- For integration details, see [Supported CDNs](supported-cdns.md).-->

## Ondersteunde CDN-tokenisatieschema&#39;s {#cdn-tokenization-schemes}

CDN&#39;s hebben vaak verschillende tokenisatieschema&#39;s voor fragmentautorisatie. Primetime Ad Insertion steunt nationaal belangrijke netwerken CDN, die omvatten:

* Akamai
* Lichtsterkte
* Centurylink / Niveau3
* Neem contact op met uw ondersteuningsvertegenwoordiger voor Primetime voor een volledige lijst met ondersteunde CDN&#39;s

Voor meer informatie over de `pttoken` parameter, zie [Bootstrap API parameterbeschrijving](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md).

## Advertenties configureren om te leveren vanuit de CDN-inhoud {#configure-ad-deliver-from-cdn}

Mogelijk wilt u advertenties en inhoud van dezelfde CDN leveren om de affiniteit van inhoud te behouden, zodat gebruikers de inhoud kunnen omzeilen en blokkeren en/of het aantal vereiste verbindingen van de clienttoepassing kunnen optimaliseren. Primetime Ad Insertion ondersteunt fragmentherschrijvingsregels om fragmenten toe te wijzen aan uw CDN-inhoud.

<!--## Increase start-up performance with your CDN {#increase-startup-performance}

For more information, see [Optimizing start-up](optimize-video-startup-time.md).-->

## MultiCDN-functies {#enable-multi-cdn-fetures}

Neem contact op met uw vertegenwoordiger van Primetime-ondersteuning om functies voor meerdere CDN&#39;s in te schakelen.
