---
description: Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.
title: Beleid instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Beleid instellen{#setting-policies}

Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.

Het maken van beleid maakt deel uit van uw verzoek voor licentietoken. (Zie [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) bijvoorbeeld Widevine).

Als de server-side code van een klant heeft bepaald dat deze een licentie zal uitgeven (op basis van machtigingscontroles, geolocatie of andere vereiste informatie), wordt een token gevraagd en *in het token* de vereiste `securityLevel`, `hdcpOutputControl`, en `licenseDuration`. Dat zijn de opties aan de clientzijde voor een Widevine-beleid. Andere DRM-oplossingen bieden vergelijkbare benaderingen, maar de details verschillen per geval en worden in de afzonderlijke workflows nader uitgewerkt.

>[!NOTE]
>
>Adobe biedt een voorbeeldreferentieserver die laat zien hoe u uw eigen machtigingsserver/-opslagront implementeert: [Referentieserver: Sample ExpressPlay Entitlement Server (SES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)
