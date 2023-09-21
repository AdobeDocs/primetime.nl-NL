---
description: Een opportuniteitsgenerator identificeert plaatsingsmogelijkheden door douanetags in een stream, en aangepaste markeringen voor de signaalmodus enzovoort. De opportuniteitsgenerator verzendt deze plaatsingskansen naar de contentoplosser, die de workflow voor inhouds- en invoegtoepassingen aanpast op basis van de eigenschappen en metagegevens van de plaatsingsmogelijkheid.
title: Aanpassen van opportuniteitsgeneratoren en contentoplossers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Overzicht {#customize-opportunity-generators-and-content-resolvers-overview}

Een opportuniteitsgenerator identificeert plaatsingsmogelijkheden door douanetags in een stream, en aangepaste markeringen voor de signaalmodus enzovoort. De opportuniteitsgenerator verzendt deze plaatsingskansen naar de contentoplosser, die de workflow voor inhouds- en invoegtoepassingen aanpast op basis van de eigenschappen en metagegevens van de plaatsingsmogelijkheid.

TVSDK bevat de volgende standaardopportuniteitsgeneratoren:

* `ManifestCuesOpportunityGenerator` Hiermee worden mogelijkheden gegenereerd op basis van de standaard en cues ( `#EXT-X-CUE`).

* `AdSignalingModeOpportunityGenerator` genereert een eerste mogelijkheid voor de opgegeven advertentiemodus. Hiermee worden aanwijzingen of metagegevens met tijdslimiet genegeerd.
* `CustomMarkerOpportunityGenerator` Hiermee worden mogelijkheden gegenereerd om ingeleverde C3-advertenties te vervangen.
* `AuditudeResolver`De opportuniteitsgenerator biedt kansen wanneer luie en het oplossen ingeschakeld is.

TVSDK bevat ook standaardinhoudsoplosmiddelen:

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`, die kan communiceren met Primetime en besluitvorming.

U kunt de standaardopportuniteitsgenerators en -oplossers negeren en zo de advertentieworkflow als volgt aanpassen:

* Eigen tags herkennen voor invoegen van advertentie
* Maak een aangepaste advertentieprovider.
* Inhoud onleesbaar maken
