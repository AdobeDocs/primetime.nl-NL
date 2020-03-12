---
description: Een opportuniteitsdetector is een TVADK-component die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.
seo-description: Een opportuniteitsdetector is een TVADK-component die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.
seo-title: Aangepaste opportuniteitsdetectors en contentoplossers
title: Aangepaste opportuniteitsdetectors en contentoplossers
uuid: 7bd04c8f-6f04-4321-88e8-9bb93251d940
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Overzicht {#customize-opportunity-detectors-and-content-resolvers-overiew}

Een opportuniteitsdetector is een TVADK-component die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.

TVSDK bevat standaard opportuniteitsdetectoren:

* `SpliceOutOpportunityDetector`, die standaard en aanwijzingen begrijpt
* `AdSignalingModeOpportunityGenerator`, die verantwoordelijk is voor het creëren van initiële en plaatsingsmogelijkheden op basis van de advertentiemodus
* `SpliceOutOpportunityGenerator`, die verantwoordelijk is voor het maken van plaatsingsmogelijkheden op basis van elke #EXT-X-CUE-tag

TVSDK bevat ook een standaardinhoudsoplosser die inhoud bevat die moet worden ingevoegd op basis van de metagegevenssleutel in het speleritem:

* `AuditudeResolver`, in staat om te communiceren met Adobe Primetime en beslissingsservers (voorheen bekend als Auditude) en om ad-hocafbrekingen te retourneren die moeten worden geplaatst.

U kunt de standaardopportuniteitsdetectors en inhoudsoplossers overschrijven om de advertentieworkflow op de volgende manieren aan te passen:

* Ondersteuning voor aangepaste tagdetectie toevoegen
* Eigen tags herkennen voor invoegen van advertentie
* Een aangepaste advertentieprovider maken
* Inhoud onleesbaar maken

