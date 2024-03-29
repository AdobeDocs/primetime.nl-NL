---
description: TVSDK voor Desktop HLS omvat een verscheidenheid van eigenschappen en verstrekt de volgende belangrijkste mogelijkheden
title: Functies van Primetime TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Functies van Primetime TVSDK{#primetime-tvsdk-features}

TVSDK voor Desktop HLS omvat een verscheidenheid van eigenschappen en verstrekt de volgende belangrijkste mogelijkheden:

* VOD en live/lineair afspelen

   * Beheer van het afspeelvenster, inclusief methoden om de positie van de afspeelkop af te spelen, te stoppen, te pauzeren, te zoeken en op te halen.
   * Ondertiteling (608, 708, WebVTT) en alternatieve vormen van audio voor verhoogde toegankelijkheid
   * Besturingselement voor tekstopmaak in bijschriften
   * DVR-mogelijkheid, snel vooruit/snel terugspoelen (truc-play modus)
   * Stekelspel voor zowel live- als VOD-inhoud
   * Adaptive bit rate (ABR) logica en eerste instelling van ABR-besturingselementen
   * Ondersteuning voor failover van Live manifest
   * Aanpasbare afspeelbuffers
   * 302 Redirect optimization
   * Ondersteuning voor het bijhouden van de duur, de grootte en de tijd-tot-downloadtijd van fragmenten

* Reclame

   * VPAID 2.0
   * Client en stitching

      * Naadloze invoeging, inclusief ondersteuning voor VAST/VMAP
      * Ondersteuning voor aangepaste actietags voor advertenties
      * Ondersteuning voor het markeren, vervangen en verwijderen van C3-advertenties
      * Aanpasbare workflow voor het plaatsen van inhoud/toevoegingen, inclusief uitschakeling

* Inhoudsbescherming

   * Toegang tot DRM-gerelateerde diensten (Digital Rights Management)
   * Afspelen van HLS-streams zonder codering of met Protected HTTP Live Streaming (PHLS)
   * Op resolutie-gebaseerde outputcontrole, die op beleid DRM wordt gebaseerd
   * Sessiecookie en ondersteuning voor audioframes
   * Meerdomeintoken verpakken

* Video en advertentie bijhouden

   * QoS-gebeurtenis bijhouden
   * Meldingen die TVSDK en uw toepassing helpen om asynchroon over de status van video&#39;s, advertenties, en andere elementen, en ook die logboekactiviteit te communiceren.
   * Integratie met Adobe Analytics en ondersteuning voor hartslagen

* Logboekregistratie

   * Foutopsporingslogbestand.
   * Ondersteuning voor reeksspatiëring voor de duur, de grootte en de downloadtijd van fragmenten.
