---
description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
title: banneradvertenties weergeven
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# banneradvertenties weergeven {#display-banner-ads}

Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.

TVSDK biedt een lijst met banneradvertenties voor gezellen die via de `AdPlaybackEventListener.onAdBreakStart` gebeurtenis.

Manifests kunnen banneradvertenties voor gezellen specificeren door:

* Een HTML-fragment
* De URL van een iFrame-pagina
* De URL van een statisch of Adobe Flash-SWF-bestand

Voor elke bijbehorende advertentie geeft TVSDK aan welke typen beschikbaar zijn voor uw toepassing.

1. Voeg een listener toe voor de `AdPlaybackEventListener.onAdBreakStart` gebeurtenis die het volgende doet:

   * Wist bestaande advertenties in de bannerinstantie.
   * Hiermee wordt de lijst met bijbehorende advertenties opgehaald van `Ad.getCompanionAssets`.
   * Doorloop de lijst voor bannerinstanties als de lijst met bijbehorende advertenties niet leeg is.

     Elke bannerinstantie (een `AdAsset`) bevat informatie, zoals breedte, hoogte, middeltype (html, iframe, of statisch), en gegevens die wordt vereist om de bijbehorende banner te tonen.
   * Als een video zonder bijbehorende advertenties is geboekt, bevat de lijst met bijbehorende elementen geen gegevens voor die video-advertentie.
   * Als u een standalone weergaveadvertentie wilt weergeven, voegt u de logica toe aan uw script om een normale DFP-advertentie (DoubleClick voor Publishers) in de juiste bannerinstantie uit te voeren.
   * Verzendt de bannergegevens naar een functie op de pagina die de banners op een geschikte locatie weergeeft.

     Dit is meestal een `div`en uw functie gebruikt de `div ID` de banner weergeven.
