---
description: TVSDK voor Android 2.5 bevat diverse functies die u kunt implementeren in uw spelers.
title: Functies van Primetime TVSDK
exl-id: 1f1ea807-67b0-4dfa-adf3-198207f57aff
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Functies van Primetime TVSDK {#primetime-tvsdk-features}

TVSDK voor Android 2.7 bevat diverse functies die u kunt implementeren in uw spelers.

TVSDK-mogelijkheden:

* **VOD en live/lineair afspelen**

   * Beheer van het afspeelvenster, inclusief methoden om de positie van de afspeelkop af te spelen, te stoppen, te pauzeren, te zoeken en op te halen
   * Ondersteuning voor volledig afspelen van gebeurtenissen
   * Ondertiteling (608, 708, WebVTT) en alternatieve vormen van audio voor verhoogde toegankelijkheid
   * Besturingselementen voor tekstopmaak in bijschriften
   * DVR-mogelijkheid, snel vooruit en snel terugspoelen (de laatste twee worden ook wel *truc-afspeelmodus*)
   * Adaptive bit rate (ABR) logica en eerste instelling van ABR-besturingselementen
   * Ondersteuning voor failover van Live manifest
   * Aanpasbare afspeelbuffers
   * De duur, de grootte en de tijd-aan-download steun van het fragment volgen

* **Reclame**

   * VPAID 2.0
   * Client en stitching

      * Naadloze invoeging, inclusief ondersteuning voor VAST/VMAP
      * Ondersteuning voor aangepaste actietags voor advertenties
      * Ondersteuning voor het markeren, vervangen en verwijderen van C3-advertenties
      * Aanpasbare workflow voor het plaatsen van inhoud/toevoegingen, inclusief uitschakeling

* **Inhoudsbescherming**

   * Toegang tot DRM-gerelateerde diensten
   * Afspelen van HLS-streams zonder codering of met Protected HTTP Live Streaming (PHLS)
   * Op resolutie-gebaseerde outputcontrole, die op beleid DRM wordt gebaseerd

* **Video en advertentie bijhouden**

   * QoS-gebeurtenis bijhouden
   * Meldingen die TVSDK en uw toepassing helpen om asynchroon over de status van video&#39;s, advertenties en andere elementen te communiceren. Meldingen registreren ook activiteit.

* **Logboekregistratie**

   * Foutopsporingsregistratie
   * Ondersteuning voor reeksspatiëring voor de duur, de grootte en de downloadtijd van fragmenten.
