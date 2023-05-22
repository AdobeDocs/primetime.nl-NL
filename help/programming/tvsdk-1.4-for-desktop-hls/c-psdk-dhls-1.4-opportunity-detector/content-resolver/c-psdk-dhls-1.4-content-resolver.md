---
description: Een opportuniteitsdetector is een TVADK-component die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.
title: Aangepaste opportuniteitsdetectors en contentoplossers
exl-id: 0721278c-e128-4afc-ae81-4f23c2644859
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Overzicht {#customize-opportunity-detectors-and-content-resolvers-overiew}

Een opportuniteitsdetector is een TVADK-component die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.

TVSDK bevat standaard opportuniteitsdetectoren:

* `SpliceOutOpportunityDetector`, die standaard en aanwijzingen begrijpt
* `AdSignalingModeOpportunityGenerator`, die verantwoordelijk is voor het creëren van initiële en plaatsingsmogelijkheden op basis van de advertentiemodus
* `SpliceOutOpportunityGenerator`, die verantwoordelijk is voor het maken van plaatsingsmogelijkheden op basis van elke #EXT-X-CUE-tag

TVSDK bevat ook een standaardinhoudsoplosser die inhoud bevat die moet worden ingevoegd op basis van de metagegevenssleutel in het speleritem:

* `AuditudeResolver`, geschikt voor communicatie met Adobe Primetime en beslissingsservers (voorheen Auditude genoemd) en het retourneren van ad-hoconderbrekingen die moeten worden geplaatst.

U kunt de standaardopportuniteitsdetectors en inhoudsoplossers overschrijven om de advertentieworkflow op de volgende manieren aan te passen:

* Ondersteuning voor aangepaste tagdetectie toevoegen
* Eigen tags herkennen voor invoegen van advertentie
* Een aangepaste advertentieprovider maken
* Inhoud onleesbaar maken
