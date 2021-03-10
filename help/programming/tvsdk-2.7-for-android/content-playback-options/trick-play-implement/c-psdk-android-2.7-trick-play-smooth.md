---
description: Als uw systeem toegang heeft tot decodering met hardwareondersteuning, kunt u met de iFrame-indeling beter truc's afspelen dan met de zuivere software-TVSDK-implementatie.
title: Vloeiende truckbewerkingen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---


# Vloeiende truckbewerkingen {#smoother-trick-play-operations}

Als uw systeem toegang heeft tot decodering met hardwareondersteuning, kunt u met de iFrame-indeling beter truc&#39;s afspelen dan met de zuivere software-TVSDK-implementatie.

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

Het gebruik van de iFrame-indeling resulteert in &#39;truc play&#39;-bewerkingen die niet vloeiend zijn. Voor een vloeiender truckplay-bewerking wordt een normaal (geen iFrame) profiel, ondersteuning voor hardwaredecodering en een hogere framesnelheid gebruikt. Verschillende decoderingsapparaten met hardwareondersteuning hebben verschillende mogelijkheden. De dubbele snelheid vereist 60 kaders per seconde (FPS), en de viervoudige snelheid vereist 120 FPS.

>[!IMPORTANT]
>
>Adobe raadt u aan het afspelen te beperken tot dubbele snelheid voor nieuwere Android-apparaten en de functie niet te gebruiken voor oudere Android-apparaten.

Om een vlotter kunstspel te bereiken, plaats `ABRControlParameters.maxPlayoutRate` aan de gewenste veelvoud van normale snelheid (bijvoorbeeld, 2.0 voor dubbele snelheid). Als een volgende aanroep van `MediaPlayer.setRate()` een argument heeft dat minder dan of gelijk aan de waarde u voor `maxPlayoutRate` plaatst, gebruikt TVSDK een normaal profiel om vlotter kunstspel te bereiken. Anders wordt een iFrame-profiel gebruikt voor de trickplay-bewerking.
