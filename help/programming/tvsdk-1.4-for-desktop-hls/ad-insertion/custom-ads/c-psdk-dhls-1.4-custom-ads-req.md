---
description: VPAID (Video Player Ad-Serving Interface Definition) biedt een algemene interface voor het afspelen van videoadvertenties. VPAID biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, afbeeldingen bij te houden en te drukken en video-inhoud te monetiseren.
seo-description: VPAID (Video Player Ad-Serving Interface Definition) biedt een algemene interface voor het afspelen van videoadvertenties. VPAID biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, afbeeldingen bij te houden en te drukken en video-inhoud te monetiseren.
seo-title: Aangepaste vereisten voor advertenties
title: Aangepaste vereisten voor advertenties
uuid: 6d4ba87b-ffe5-467d-8ab5-9795928c2f69
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Aangepaste vereisten voor advertenties {#custom-ad-requirements}

De TVSDK-speler kan VPAID-advertenties (Digital Video Player Ad-Interface Definition) afspelen en de laadstatus van de advertentie weergeven. Als de advertentie fouten bevat of het laden van advertenties te lang duurt, negeert TVSDK deze advertenties.

VPAID (Video Player Ad-Serving Interface Definition) biedt een algemene interface voor het afspelen van videoadvertenties. VPAID biedt gebruikers een rijke mediabeleving en biedt uitgevers de mogelijkheid om advertenties beter te richten, afbeeldingen bij te houden en te drukken en video-inhoud te monetiseren.

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

De TVSDK ondersteunt de volgende functies:

* Versie 1.0 en 2.0 van de VPAID-specificatie
* Lineaire VPAID-advertenties op video-on-demand (VOD)-inhoud
* Flash VPAID-advertenties

   VPAID-advertenties moeten zijn gebaseerd op Flash en de reactie op de advertentie moet het mediatype van de VPAID-advertentie identificeren als `application/x-shockwave-flash`.

De volgende functies worden niet ondersteund:

* Niet-onlineadvertenties zoals overlayadvertenties en dynamische bijbehorende advertenties
* VPAID-advertenties vooraf laden
* VPAID-advertenties in live-inhoud
* JavaScript VPAID-advertenties

## Status van laden {#section_5F55C0101CD44A65BCFE1D124CBDF239}

De TVSDK verzendt de volgende gebeurtenissen:

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

Na de `AdStopped` gebeurtenis wordt de video-inhoud door de TVSDK hervat.

>[!TIP]
>
>Als u de waarde nul opgeeft, probeert TVSDK de advertentie te laden totdat deze wordt geladen of een fout is opgetreden.

## Advertenties negeren {#section_3EA452F420884335AE90DF23C17E416A}

Als de advertentie te lang duurt om te laden of als er fouten in de advertentie voorkomen, kan de TVSDK de advertentie negeren en wordt de volgende advertentie in de advertentiepod automatisch afgespeeld.

Als de `AuditudeSettings.customAdLoadTimeout` instelling een aantal seconden groter dan nul opgeeft, probeert de TVSDK de advertentie naar de opgegeven duur te laden. Als de advertentie niet kan worden geladen, wordt de advertentie overgeslagen. Bijvoorbeeld, als u vormt `AuditudeSettings.customAdLoadTimeout:5`, probeert TVSDK om de advertentie voor een maximum van 5 seconden te laden. Als de advertentie nog steeds niet wordt geladen, wordt deze genegeerd.
