---
description: TVSDK voor Android 2.5 bevat diverse functies die u kunt implementeren in uw spelers.
seo-description: TVSDK voor Android 2.5 bevat diverse functies die u kunt implementeren in uw spelers.
seo-title: Functies van Primetime TVSDK
title: Functies van Primetime TVSDK
uuid: 20ef9abf-1a33-4afc-bb2e-4910e3398a7a
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Functies van Primetime TVSDK {#primetime-tvsdk-features}

TVSDK voor Android 2.7 bevat diverse functies die u kunt implementeren in uw spelers.

TVSDK-mogelijkheden:

* **VOD en live/lineair afspelen**

   * Beheer van het afspeelvenster, inclusief methoden om de positie van de afspeelkop af te spelen, te stoppen, te pauzeren, te zoeken en op te halen
   * Ondersteuning voor volledig afspelen van gebeurtenissen
   * Ondertiteling (608, 708, WebVTT) en alternatieve vormen van audio voor verhoogde toegankelijkheid
   * Besturingselementen voor tekstopmaak in bijschriften
   * DVR-mogelijkheid, snel vooruit en snel terugspoelen (de laatste twee zijn bekend als *truc-afspeelmodus*)
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