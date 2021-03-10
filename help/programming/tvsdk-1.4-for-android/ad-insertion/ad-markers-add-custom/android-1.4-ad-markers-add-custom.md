---
description: Door aangepaste advertentiemarkeringen te gebruiken, kunt u specifieke gedeelten van de hoofdinhoud markeren als aan een advertentie gerelateerde inhoudsperioden.
title: Aangepaste advertentiemarkeringen toevoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Overzicht {#add-custom-ad-markers-overview}

Door aangepaste advertentiemarkeringen te gebruiken, kunt u specifieke gedeelten van de hoofdinhoud markeren als aan een advertentie gerelateerde inhoudsperioden.

Deze functie is vooral handig wanneer inhoud wordt opgenomen van bijvoorbeeld een livegebeurtenis en het resultaat van de opname één HLS-stream is. De opname bevat de belangrijkste inhoud en inhoud met betrekking tot reclame in één HLS video-op-vraag (VOD) stroom. Tijdens het opnameproces worden de ad-gerelateerde segmenten niet bijgehouden, zodat de informatie die betrekking heeft op de plaatsing van de advertenties in de hoofdinhoud verloren gaat.

Mogelijk kunt u de informatie die betrekking heeft op de positie van de periode van ad-inhoud opvragen bij andere out-of-band bronnen, zoals externe CMS-systemen. U kunt aangepaste markeertekens definiëren waarmee deze out-of-band informatie kan worden doorgegeven aan het tijdlijnbeheersubsysteem. Het is de bedoeling om de inhoudssecties te markeren die overeenkomen met de opgegeven inhoud met betrekking tot advertentie, zodat alle ad-specifieke afspeelgebeurtenissen op dezelfde manier worden geactiveerd als wanneer deze aangepaste tijdvakken expliciet op de tijdlijn van de speler werden geplaatst.

Het bijhouden van advertenties wordt niet intern afgehandeld door TVSDK, bijvoorbeeld wanneer advertenties worden opgelost door Adobe Primetime en door een beslissing (voorheen Auditude). TVSDK biedt echter de volgende abstracties die bepalen hoe ad-gerelateerde inhoud op de tijdlijn wordt weergegeven:

* Het ad-einde

   Een advertentie-einde is een geordende lijst met afzonderlijke opeenvolgende advertenties.
* Een individuele advertentie

Afspeelgebeurtenissen worden afzonderlijk geactiveerd voor ad-einden en advertenties op het begin- en eindpunt voor elke advertentie.

TVSDK verzendt en volgt gebeurtenissen naar uw toepassing, zodat u uw eigen traceringslogica kunt implementeren. Als u aangepaste advertentiemarkeringen instelt, ontvangt u de gebeurtenissen `onAdBreakStart`, `onAdStart`, `onAdProgress`, `onAdComplete` en `onAdBreakComplete`.
