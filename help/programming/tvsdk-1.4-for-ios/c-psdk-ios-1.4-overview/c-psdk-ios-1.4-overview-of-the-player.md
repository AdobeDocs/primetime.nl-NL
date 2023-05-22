---
description: TVSDK voor iOS bevat verschillende functies.
title: Functies van Primetime TVSDK
exl-id: 1968c072-2651-442d-9e4c-412f7959bcab
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Functies van Primetime TVSDK {#primetime-tvsdk-features}

TVSDK voor iOS bevat verschillende functies en biedt de volgende hoofdmogelijkheden:

* VOD en live/lineair afspelen

   * Beheer van het afspeelvenster, inclusief methoden om de positie van de afspeelkop af te spelen, te stoppen, te pauzeren, te zoeken en op te halen
   * Ondersteuning voor volledig afspelen van gebeurtenissen
   * Ondertiteling (608, WebVTT) en alternatieve vormen van audio voor verhoogde toegankelijkheid
   * DVR-mogelijkheid
   * Adaptive bit rate (ABR) logica en eerste instelling van ABR-besturingselementen
   * Abonnement op niet-HLS- en HLS-tags
   * Ondersteuning voor failover van Live manifest

* Reclame

   * VPAID 2.0
   * Client en stitching

      * Naadloze invoeging, inclusief ondersteuning voor VAST/VMAP
      * Ondersteuning voor aangepaste actietags voor advertenties
      * Ondersteuning voor het markeren, vervangen en verwijderen van C3-advertenties
      * Aanpasbare workflow voor het plaatsen van inhoud/toevoegingen, inclusief uitschakeling

* Inhoudsbescherming

   * Toegang tot DRM-gerelateerde diensten
   * Afspelen van HLS-streams zonder codering of met Protected HTTP Live Streaming (PHLS)
   * Op resolutie-gebaseerde outputcontrole, die op beleid DRM wordt gebaseerd

* Video en advertentie bijhouden

   * QoS-gebeurtenis bijhouden
   * Meldingen die TVSDK en uw toepassing helpen om asynchroon over de status van video&#39;s, advertenties, en andere elementen te communiceren, en ook die logboekactiviteit
   * Integratie met Adobe Analytics en ondersteuning voor hartslagen

* Logboekregistratie

   * Foutopsporingsregistratie
