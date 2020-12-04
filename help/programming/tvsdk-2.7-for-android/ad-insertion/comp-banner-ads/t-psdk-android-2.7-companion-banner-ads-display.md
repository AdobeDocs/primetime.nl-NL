---
description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
seo-description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
seo-title: banneradvertenties weergeven
title: banneradvertenties weergeven
uuid: 7246dfab-860f-4b55-9554-49738a483406
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# banneradvertenties {#display-banner-ads} weergeven

Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.

TVSDK biedt een lijst met banneradvertenties die bij een lineaire advertentie horen via de gebeurtenis `AdPlaybackEventListener.onAdBreakStart`.

Manifests kunnen banneradvertenties voor gezellen specificeren door:

* Een HTML-fragment
* De URL van een iFrame-pagina
* De URL van een statische afbeelding of een Adobe Flash-SWF-bestand

Voor elke bijbehorende advertentie geeft TVSDK aan welke typen beschikbaar zijn voor uw toepassing.

1. Voeg een listener toe voor de gebeurtenis `AdPlaybackEventListener.onAdBreakStart` die het volgende doet:

   * Wist bestaande advertenties in de bannerinstantie.
   * Haalt de lijst met bijbehorende advertenties op van `Ad.getCompanionAssets`.
   * Doorloop de lijst voor bannerinstanties als de lijst met bijbehorende advertenties niet leeg is.

      Elke bannerinstantie (een `AdAsset`) bevat informatie, zoals breedte, hoogte, middeltype (html, iframe, of statisch), en gegevens die worden vereist om de bijbehorende banner te tonen.
   * Als een video zonder bijbehorende advertenties is geboekt, bevat de lijst met bijbehorende elementen geen gegevens voor die video-advertentie.
   * Als u een standalone weergaveadvertentie wilt weergeven, voegt u de logica toe aan uw script om een normale DFP-advertentie (DoubleClick voor Publishers) in de juiste bannerinstantie uit te voeren.
   * Verzendt de bannergegevens naar een functie op de pagina die de banners op een geschikte locatie weergeeft.

      Dit is gewoonlijk een `div`, en uw functie gebruikt `div ID` om de banner te tonen.

