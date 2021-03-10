---
description: U kunt het videogebruik volgen door Browser TVSDK met Adobe Analytics te integreren.
title: Videoanalyse
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Videoanalyse{#video-analytics}

U kunt het videogebruik volgen door Browser TVSDK met Adobe Analytics te integreren.

Bij het bijhouden van video&#39;s in TVSDK van de browser wordt de service **Adobe Analytics Video Essentials** gebruikt. Deze service biedt meetgegevens voor de videobetrokkenheid, zoals videoweergaven, voltooide video en indrukkingen, aan video bestede tijd, enzovoort. Neem voor meer informatie over deze service contact op met uw Adobe-vertegenwoordiger.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video volgende componenten:

   * **AppMeasurement-bibliotheek** : bevat de kernlogica voor het verzamelen van gegevens op laag niveau. Dit is waar de videohartslaggegevens worden verzameld en over het netwerk verzonden.
   * **Videohartslagbibliotheek**  - Bevat de kernlogica van de videohartslaggegevensverzameling. De videohartslagbibliotheek heeft toegang tot een subset van de API&#39;s van de AppMeasurement-bibliotheek.

      >[!TIP]
      >
      >Uw app communiceert niet rechtstreeks met de videohartslagcode. In plaats daarvan gebruikt de app TVSDK-API&#39;s van de browser om de mogelijkheden voor het bijhouden van video&#39;s van uw speler te configureren.

   * **BezoekerID-bibliotheek** : geeft bezoekers op unieke wijze aan op de webpagina waarop de videospeler wordt gehost.
   >[!IMPORTANT]
   >
   >De ingebouwde mogelijkheid voor videotracering van de Browser-TVSDK is afhankelijk van een correct geconfigureerde AppMeasurement-instantie. De volgende elementen veronderstellen dat de bibliotheek AppMeasurement reeds wordt geconcretiseerd en gevormd alvorens video het volgen te vormen en te activeren. De mogelijkheden voor het bijhouden van video&#39;s van TVSDK van de browser zijn afhankelijk van het bestaan van een volledig functionele en correct geconfigureerde instantie van de AppMeasurement-bibliotheek.

1. Stel met Adobe Analytics Admin Tools videoanalytics in die rapporteren op de server.