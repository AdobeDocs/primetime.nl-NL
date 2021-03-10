---
description: Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.
title: Beleid instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Beleid instellen{#setting-policies}

Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.

Het creëren van beleid komt als deel van uw verzoek van het licentietoken voor. (Zie [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) voor een voorbeeld dat Widevine gebruikt).

Zodra de server-side code van een klant heeft bepaald dat hij een licentie zal uitgeven (op basis van aanbetalingscontroles, geolocatie of andere vereiste informatie), vraagt hij om een token en *in het token* geeft het de vereiste `securityLevel`, `hdcpOutputControl` en `licenseDuration` aan. Dat zijn de opties aan de clientzijde voor een Widevine-beleid. Andere DRM-oplossingen bieden vergelijkbare benaderingen, maar de details verschillen per geval en worden in de afzonderlijke workflows nader uitgewerkt.

>[!NOTE]
>
>Adobe biedt een voorbeeldreferentieserver die laat zien hoe u uw eigen machtigingsserver/-opslagront implementeert: [Referentieserver: Sample ExpressPlay Entitlement Server (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

