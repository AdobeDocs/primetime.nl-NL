---
description: Er zijn een paar manieren om plaatsing en plaatsing van advertenties te bepalen.
seo-description: Er zijn een paar manieren om plaatsing en plaatsing van advertenties te bepalen.
seo-title: Toevoegen en plaatsen van toevoegen
title: Toevoegen en plaatsen van toevoegen
uuid: 1d4d6364-1c49-402b-9b72-8c185b1c94e1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---


# Toevoegen en plaatsen{#ad-insertion-and-placement}

Er zijn een paar manieren om plaatsing en plaatsing van advertenties te bepalen.

## Toevoegen {#section_1F7581B987704E318E064082190E8243}

Hier volgt een overzicht van het proces dat wordt gebruikt om ad-invoeging te bepalen:

1. **Opportuniteitsdetectie**: De TVSDK gebruikt stroominformatie om mogelijke en gewenste locaties voor advertenties te detecteren.
1. **Advertentieresolutie**: De TVSDK communiceert met een advertentieserver om de advertenties op te halen die in de inhoud moeten worden gesplice.
1. **Advertentie plaatsen**: De TVSDK laadt de opgegeven advertenties en plaatst deze in ad-hoconderbrekingen op de tijdlijn van de inhoud op de opgegeven locaties en berekent de virtuele tijdlijn indien nodig opnieuw.

## Plaatsing toevoegen {#section_B9D63F7409A2447F9FF209289BE5D3D5}

De TVSDK kan locaties voor mogelijke advertentie opvragen vanuit de volgende bronnen:

* **Metagegevens/aanwijzingen manifesteren**

   TVSDK detecteert de aanwijzingen, haalt de benodigde informatie uit deze aanwijzingen en communiceert met een advertentieserver om de bijbehorende advertenties op te halen. Deze bron komt veel voor bij live/lineaire streams.

   De TVSDK vervangt de hoofdinhoud doorgaans door de advertenties op de locatie die wordt aangegeven door de metagegevens/aanwijzingen. anders zou de cliënt meer en meer achter het daadwerkelijke levende punt vallen.

* **De advertentieserverkaart**

   Metagegevens over deze streams worden gewoonlijk vóór het afspelen op de advertentieserver geregistreerd. De TVSDK haalt de tijdlijn van de advertentie en de bijbehorende advertenties op van de server. Deze bron komt veel voor VOD-streams.

   De TVSDK voegt gewoonlijk de opgeloste advertenties in de belangrijkste inhoud in zoals die door de serverkaart wordt vermeld.

>[!NOTE]
>
>Standaard gebruikt de TVSDK duidelijke aanwijzingen voor live/lineaire streams en reclameservertoewijzingen voor VOD-streams. Uw toepassing moet echter extra stappen uitvoeren om het volledig afspelen van gebeurtenissen voor live gebeurtenissen te ondersteunen.

