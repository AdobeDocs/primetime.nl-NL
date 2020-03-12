---
description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
seo-description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
seo-title: banneradvertenties weergeven
title: banneradvertenties weergeven
uuid: cfd4b26c-9643-4b60-9aff-bc27dec289f1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# banneradvertenties weergeven {#display-banner-ads}

Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.

TVSDK biedt een lijst met banneradvertenties voor gezelschappen die via de `AdPlaybackEventListener.onAdBreakStart` gebeurtenis aan een lineaire advertentie zijn gekoppeld.

Manifests kunnen banneradvertenties voor gezellen specificeren door:

* Een HTML-fragment
* De URL van een iFrame-pagina
* De URL van een statische afbeelding of een Adobe Flash SWF-bestand

Voor elke bijbehorende advertentie geeft TVSDK aan welke typen beschikbaar zijn voor uw toepassing.

1. Voeg een listener toe voor de `AdPlaybackEventListener.onAdBreakStart` gebeurtenis die het volgende doet:

   * Wist bestaande advertenties in de bannerinstantie.
   * Haalt de lijst met bijbehorende advertenties op van `Ad.getCompanionAssets`.
   * Doorloop de lijst voor bannerinstanties als de lijst met bijbehorende advertenties niet leeg is.

      Elke bannerinstantie (een `AdAsset`) bevat informatie, zoals breedte, hoogte, middeltype (html, iframe of statisch), en gegevens die nodig zijn om de bijbehorende banner weer te geven.
   * Als een video zonder bijbehorende advertenties is geboekt, bevat de lijst met bijbehorende elementen geen gegevens voor die video-advertentie.
   * Als u een standalone weergaveadvertentie wilt weergeven, voegt u de logica toe aan uw script om een normale DFP-advertentie (DoubleClick voor Publishers) in de juiste bannerinstantie uit te voeren.
   * Verzendt de bannergegevens naar een functie op de pagina die de banners op een geschikte locatie weergeeft.

      Dit is meestal een `div`bewerking en uw functie gebruikt deze `div ID` om de banner weer te geven.