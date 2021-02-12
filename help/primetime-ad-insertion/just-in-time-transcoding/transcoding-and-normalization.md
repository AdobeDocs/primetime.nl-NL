---
title: Transcodering en normalisatie
description: null
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---


# Transcodering en normalisatie {#transcoding-and-normalization}

Primetime Ad Insertion probeert een consistente weergavekwaliteit te garanderen voor alle inhoud en advertenties door te proberen deze aan te passen:

1. Bronstreamcodecs en bitsnelheden, terwijl u bij het transcoderen altijd de hoogste kwaliteit/bitsnelheid selecteert

1. Bronstreamfragmentgrootten (HLS/#EXT-X-TARGETDURATION)

1. Voorkeursindelingen voor creatieve doeleinden voor transcodering

1. Audio automatisch nivelleren om te zorgen voor een consistent dB-niveau voor alle advertentiefilters.

>[!NOTE]
>
>HLS-elementen die worden gegenereerd door de Ad Insertion-just-in-time Primetime-transcodering leveren HLS-elementen van versie 3, ongeacht welke HLS-versie in de inhoud is gedefinieerd.