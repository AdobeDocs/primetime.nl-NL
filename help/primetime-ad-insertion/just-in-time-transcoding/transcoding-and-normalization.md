---
title: Transcodering en normalisatie
description: Transcodering en normalisatie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Transcodering en normalisatie {#transcoding-and-normalization}

Primetime Ad Insertion probeert een consistente weergavekwaliteit te garanderen voor alle inhoud en advertenties door te proberen deze aan te passen:

1. Bronstreamcodecs en bitsnelheden, terwijl u altijd de hoogste kwaliteit/bitsnelheid selecteert die bij het transcoderen creatief is

1. Bronstreamfragmentgrootten (HLS/#EXT-X-TARGETDURATION)

1. Voorkeursindelingen voor creatieve doeleinden voor transcodering

1. Audio automatisch nivelleren om te zorgen voor een consistent dB-niveau voor alle advertentiefilters.

>[!NOTE]
>
>HLS-elementen die worden gegenereerd door de Ad Insertion-just-in-time Primetime-transcodering leveren HLS-elementen van versie 3, ongeacht welke HLS-versie in de inhoud wordt gedefinieerd.
