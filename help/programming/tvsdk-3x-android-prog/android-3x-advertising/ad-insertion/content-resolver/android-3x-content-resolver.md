---
description: Een opportuniteitsgenerator identificeert plaatsingsmogelijkheden door douanetags in een stream, en aangepaste markeringen voor de signaalmodus enzovoort. De opportuniteitsgenerator verzendt deze plaatsingskansen naar de contentoplosser, die de workflow voor inhouds- en invoegtoepassingen aanpast op basis van de eigenschappen en metagegevens van de plaatsingsmogelijkheid.
seo-description: Een opportuniteitsgenerator identificeert plaatsingsmogelijkheden door douanetags in een stream, en aangepaste markeringen voor de signaalmodus enzovoort. De opportuniteitsgenerator verzendt deze plaatsingskansen naar de contentoplosser, die de workflow voor inhouds- en invoegtoepassingen aanpast op basis van de eigenschappen en metagegevens van de plaatsingsmogelijkheid.
seo-title: Aanpassen van opportuniteitsgeneratoren en contentoplossers
title: Aanpassen van opportuniteitsgeneratoren en contentoplossers
uuid: 0d4fb0b2-98f3-4245-9bf1-4e968c5d0f36
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

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

* Herken aangepaste tags voor het invoegen van advertenties. Voor meer informatie, zie [Aanpasbare generators en inhoudoplossers](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/content-resolver/android-3x-content-resolver.md)aanpassen.
* Maak een aangepaste advertentieprovider.
* Inhoud onleesbaar maken.