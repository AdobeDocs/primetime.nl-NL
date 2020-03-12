---
description: Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.
seo-description: Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.
seo-title: Beleid instellen
title: Beleid instellen
uuid: 2d2672ce-5ed4-4868-aa5e-0a9e21a809b3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Beleid instellen{#setting-policies}

Het instellen van een beleid is het opgeven van voorwaarden voor het moment waarop en de manier waarop een gebruiker beveiligde video-inhoud mag afspelen.

Het maken van beleid maakt deel uit van uw verzoek voor licentietoken. (Zie [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) voor een voorbeeld met Windows).

Zodra de server-zijcode van een klant heeft bepaald dat het een vergunning (die op aanbetalingscontroles, geolocatie, of andere vereiste informatie wordt gebaseerd) zal uitgeven, dan verzoekt het om een teken, en *in het teken* specificeert het vereist `securityLevel`, `hdcpOutputControl`, en `licenseDuration`. Dat zijn de opties aan de clientzijde voor een Widevine-beleid. Andere DRM-oplossingen bieden vergelijkbare benaderingen, maar de details verschillen per geval en worden in de afzonderlijke workflows nader uitgewerkt.

>[!NOTE]
>
>Adobe biedt een voorbeeldreferentieserver die laat zien hoe u uw eigen machtigingsserver/-opslagront implementeert: [Referentieserver: Voorbeeld ExpressPlay Entitlement Server (SES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

