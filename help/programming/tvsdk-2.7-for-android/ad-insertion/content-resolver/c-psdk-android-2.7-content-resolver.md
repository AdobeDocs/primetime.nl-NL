---
description: Een opportuniteitsgenerator identificeert plaatsingsmogelijkheden door douanetags in een stream, en aangepaste markeringen voor de signaalmodus enzovoort. De opportuniteitsgenerator verzendt deze plaatsingskansen naar de contentoplosser, die de workflow voor inhouds- en invoegtoepassingen aanpast op basis van de eigenschappen en metagegevens van de plaatsingsmogelijkheid.
seo-description: Een opportuniteitsgenerator identificeert plaatsingsmogelijkheden door douanetags in een stream, en aangepaste markeringen voor de signaalmodus enzovoort. De opportuniteitsgenerator verzendt deze plaatsingskansen naar de contentoplosser, die de workflow voor inhouds- en invoegtoepassingen aanpast op basis van de eigenschappen en metagegevens van de plaatsingsmogelijkheid.
seo-title: Aanpassen van opportuniteitsgeneratoren en contentoplossers
title: Aanpassen van opportuniteitsgeneratoren en contentoplossers
uuid: 97738b80-5cf8-494f-8811-449bceded220
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Overzicht {#customize-opportunity-generators-and-content-resolvers-overview}

Een opportuniteitsgenerator identificeert plaatsingsmogelijkheden door douanetags in een stream, en aangepaste markeringen voor de signaalmodus enzovoort. De opportuniteitsgenerator verzendt deze plaatsingskansen naar de contentoplosser, die de workflow voor inhouds- en invoegtoepassingen aanpast op basis van de eigenschappen en metagegevens van de plaatsingsmogelijkheid.

TVSDK bevat de volgende standaardopportuniteitsgeneratoren:

* `ManifestCuesOpportunityGenerator` genereert mogelijkheden op basis van de standaard en aanwijzingen ( `#EXT-X-CUE`).

* `AdSignalingModeOpportunityGenerator` genereert een eerste mogelijkheid voor de opgegeven advertentiemodus. Hiermee worden aanwijzingen of metagegevens met tijdslimiet genegeerd.
* `CustomMarkerOpportunityGenerator` Hiermee worden mogelijkheden gegenereerd om kant-en-klare C3-advertenties te vervangen.
* `AuditudeResolver`De opportuniteitsgenerator biedt kansen wanneer luie en het oplossen ingeschakeld is.

TVSDK bevat ook standaardinhoudsoplosmiddelen:

* `CustomRangeResolver`
* `JSONResolver`
* `AuditudeResolver`, die kan communiceren met Primetime en besluitvorming.

U kunt de standaardopportuniteitsgenerators en -oplossers negeren en zo de advertentieworkflow als volgt aanpassen:

* Eigen tags herkennen voor invoegen van advertentie
* Maak een aangepaste advertentieprovider.
* Inhoud onleesbaar maken.