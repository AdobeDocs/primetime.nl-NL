---
description: Er zijn een paar manieren om plaatsing en plaatsing van advertenties te bepalen.
title: Toevoegen en plaatsen van toevoegen
exl-id: 73f24a65-4be2-47d3-8cb9-5cb2c81e6d93
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Toevoegen en plaatsen van toevoegen{#ad-insertion-and-placement}

Er zijn een paar manieren om plaatsing en plaatsing van advertenties te bepalen.

## Toevoegen {#section_1F7581B987704E318E064082190E8243}

Hier volgt een overzicht van het proces dat wordt gebruikt om ad-invoeging te bepalen:

1. **Opportunity-detectie**: De TVSDK gebruikt stroominformatie om mogelijke en gewenste locaties voor advertenties te detecteren.
1. **Advertentieresolutie**: De TVSDK communiceert met een advertentieserver om de advertenties op te halen die in de inhoud moeten worden gesplice.
1. **Advertentie plaatsen**: De TVSDK laadt de opgegeven advertenties en plaatst deze in ad-hoconderbrekingen op de tijdlijn van de inhoud op de opgegeven locaties en berekent de virtuele tijdlijn indien nodig opnieuw.

## Advertentie plaatsen {#section_B9D63F7409A2447F9FF209289BE5D3D5}

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
