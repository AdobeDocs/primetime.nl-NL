---
title: Uw CDN integreren
description: De CDN integreren
exl-id: b93031a2-6e66-4de1-9cf2-b0260f88fe13
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Uw CDN integreren {#integrating-cdn}

Primetime Ad Insertion fungeert als een proxy tussen uw clienttoepassing en manifests, niet de videoblokken zelf. Implementeer uw inhoud naar de CDN van uw keuze en geef de URL door aan Primetime Ad Insertion met behulp van de Bootstrap-API. Voor integratiegegevens raadpleegt u [Ondersteunde CDN&#39;s](/help/primetime-ad-insertion/technical-reference/supported-cdns.md).

## Ondersteunde CDN-tokenisatieschema&#39;s {#cdn-tokenization-schemes}

CDN&#39;s hebben vaak verschillende tokenisatieschema&#39;s voor fragmentautorisatie. Primetime Ad Insertion steunt nationaal belangrijke netwerken CDN, die omvatten:

* Akamai
* Lichtsterkte
* Centurylink / Niveau3
* Neem contact op met uw ondersteuningsvertegenwoordiger voor Primetime voor een volledige lijst met ondersteunde CDN&#39;s

Voor meer informatie over de `pttoken` parameter, zie [Beschrijving van Bootstrap API-parameter](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md#parameter-description).

## Advertenties configureren om te leveren vanuit de CDN-inhoud {#configure-ad-deliver-from-cdn}

Mogelijk wilt u advertenties en inhoud van dezelfde CDN leveren om de affiniteit van inhoud te behouden, zodat gebruikers de inhoud kunnen omzeilen en blokkeren en/of het aantal vereiste verbindingen van de clienttoepassing kunnen optimaliseren. Primetime Ad Insertion ondersteunt fragmentherschrijvingsregels om fragmenten toe te wijzen aan uw CDN-inhoud. Zie voor meer informatie [Manifest re-writing](/help/primetime-ad-insertion/technical-reference/manifest-rewriting.md).

## Start-upprestaties verbeteren met uw CDN {#increase-startup-performance}

Zie voor meer informatie [Starten optimaliseren](/help/primetime-ad-insertion/best-practices/optimize-video-startup-time.md).

## Multi-CDN-functies {#enable-multi-cdn-fetures}

Neem contact op met uw vertegenwoordiger van Primetime-ondersteuning om functies voor meerdere CDN&#39;s in te schakelen.
