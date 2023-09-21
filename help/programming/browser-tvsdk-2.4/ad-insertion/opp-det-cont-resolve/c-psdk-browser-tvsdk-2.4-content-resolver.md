---
description: Een opportuniteitsdetector is een TVSDK-component van Browser die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.
title: Aangepaste opportuniteitsdetectors en contentoplossers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Overzicht {#customize-opportunity-detectors-and-content-resolvers-overview}

Een opportuniteitsdetector is een TVSDK-component van Browser die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.

Browser TVSDK bevat de volgende standaardopportuniteitsdetectoren:

* `AdSignalingModeOpportunityGenerator`, die initiële en plaatsingsmogelijkheden creëert op basis van de advertentiemodus.
* `ManifestCuesOpportunityGenerator`, die plaatsingsmogelijkheden van om het even welke splice-out markering tot stand brengt.

Browser TVSDK bevat ook standaardinhoudsoplossers, zoals `AuditudeResolver`, die inhoud bevat die wordt ingevoegd op basis van de metagegevenssleutel in het Player-item. `AuditudeResolver` kan communiceren met Adobe Primetime en beslissingsservers en kan ad-hoconderbrekingen retourneren die moeten worden geplaatst.

U kunt de standaardopportuniteitsdetectors en inhoudsoplossers overschrijven om de advertentieworkflow op de volgende manieren aan te passen:

* Ondersteuning voor aangepaste tagdetectie toevoegen
* Eigen tags herkennen voor invoegen van advertentie
* Een aangepaste advertentieprovider maken
