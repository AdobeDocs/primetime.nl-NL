---
description: Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.
title: Beleid instellen
exl-id: ab7295c8-88f2-4d4a-a7f1-3332df7bb735
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
>Adobe biedt een voorbeeldreferentieserver die laat zien hoe u uw eigen machtigingsserver/-opslagront implementeert: [Referentieserver: Voorbeeld ExpressPlay Entitlement Server (SES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)
