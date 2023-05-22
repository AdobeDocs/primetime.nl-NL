---
description: Als uw systeem toegang heeft tot decodering met hardwareondersteuning, kunt u met de iFrame-indeling beter truc's afspelen dan met de zuivere software-TVSDK-implementatie.
title: Vloeiende truckbewerkingen
exl-id: 2dcc8ee2-78a1-4ec8-b876-e06e5ec1e398
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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

Voor een vloeiender truckplay stelt u `ABRControlParameters.maxPlayoutRate` naar de gewenste veelvoud van de normale snelheid (bijvoorbeeld 2,0 voor dubbele snelheid). Als een volgende oproep tot `MediaPlayer.setRate()` heeft een argument dat kleiner is dan of gelijk is aan de waarde waarvoor u instelt `maxPlayoutRate`, gebruikt TVSDK een normaal profiel voor vloeiender truc. Anders wordt een iFrame-profiel gebruikt voor de trickplay-bewerking.
