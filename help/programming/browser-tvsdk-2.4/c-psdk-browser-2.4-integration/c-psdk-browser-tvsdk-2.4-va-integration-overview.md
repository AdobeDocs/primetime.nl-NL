---
description: U kunt het videogebruik volgen door Browser TVSDK met Adobe Analytics te integreren.
title: Videoanalyse
exl-id: b6fb39a9-6cb8-4498-a9fa-0ea19af52a58
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Videoanalyse{#video-analytics}

U kunt het videogebruik volgen door Browser TVSDK met Adobe Analytics te integreren.

Video-tracking in Browser-TVSDK gebruikt de **Adobe Analytics Video Essentials** service, die metriek voor videobetrokkenheid biedt, zoals videoweergaven, voltooide video en indrukken, tijd die aan video wordt besteed, enzovoort. Neem voor meer informatie over deze service contact op met uw Adobe-vertegenwoordiger.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video volgende componenten:

   * **AppMeasurement-bibliotheek** - Bevat de basislogica voor gegevensverzameling op laag niveau. Dit is waar de videohartslaggegevens worden verzameld en over het netwerk verzonden.
   * **Videohartslagbibliotheek** - Bevat de kernlogica voor het verzamelen van videohartslaggegevens. De videohartslagbibliotheek heeft toegang tot een subset van de API&#39;s van de AppMeasurement-bibliotheek.

      >[!TIP]
      >
      >Uw app communiceert niet rechtstreeks met de videohartslagcode. In plaats daarvan gebruikt de app TVSDK-API&#39;s van de browser om de mogelijkheden voor het bijhouden van video&#39;s van uw speler te configureren.

   * **VisitorID-bibliotheek** - Identificeert op unieke wijze bezoekers van de webpagina waarop de videospeler wordt gehost.
   >[!IMPORTANT]
   >
   >De ingebouwde mogelijkheid voor videotracering van de Browser-TVSDK is afhankelijk van een correct geconfigureerde AppMeasurement-instantie. De volgende elementen veronderstellen dat de bibliotheek AppMeasurement reeds wordt geconcretiseerd en gevormd alvorens video het volgen te vormen en te activeren. De mogelijkheden voor het bijhouden van video&#39;s van TVSDK van de browser zijn afhankelijk van het bestaan van een volledig functionele en correct geconfigureerde instantie van de AppMeasurement-bibliotheek.

1. Stel met Adobe Analytics Admin Tools videoanalytics in die rapporteren op de server.
