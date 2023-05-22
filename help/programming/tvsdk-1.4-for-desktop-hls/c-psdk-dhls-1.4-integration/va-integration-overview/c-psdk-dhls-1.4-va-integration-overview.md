---
description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
title: Videoanalyse
exl-id: 02303511-2713-4974-ada7-6f50fc500325
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Videoanalyse{#video-analytics}

U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.

Bij het bijhouden van video&#39;s in TVSDK wordt het **Adobe Analytics Video Essentials** service, die metriek voor videobetrokkenheid biedt, zoals videoweergaven, voltooide video en indrukken, tijd die aan video wordt besteed, enzovoort. Neem voor meer informatie over deze service contact op met uw Adobe-vertegenwoordiger.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video volgende componenten:

   * **AppMeasurement-bibliotheek** - Bevat de basislogica voor gegevensverzameling op laag niveau. Dit is waar de videohartslaggegevens worden verzameld en over het netwerk verzonden.
   * **Videohartslagbibliotheek** - Bevat de kernlogica voor het verzamelen van videohartslaggegevens. De videohartslagbibliotheek heeft toegang tot een subset van de `AppMeasurement` bibliotheek-API&#39;s.

      >[!TIP]
      >
      >Uw app communiceert niet rechtstreeks met de videohartslagcode. In plaats daarvan gebruikt de app TVSDK API&#39;s om de mogelijkheden voor het bijhouden van video&#39;s van uw speler te configureren.

   * **VisitorID-bibliotheek** - Identificeert op unieke wijze bezoekers van de webpagina waarop de videospeler wordt gehost.
   >[!IMPORTANT]
   >
   >De ingebouwde mogelijkheid voor videotracering voor TVSDK is afhankelijk van een correct geconfigureerde `AppMeasurement` -instantie. De volgende elementen gaan ervan uit dat de `AppMeasurement` De bibliotheek wordt reeds geconcretiseerd en gevormd alvorens video het volgen te vormen en te activeren. De mogelijkheden voor het bijhouden van TVSDK-video zijn afhankelijk van het bestaan van een volledig functionele en correct geconfigureerde instantie van de `AppMeasurement` bibliotheek.

1. Stel met Adobe Analytics Admin Tools videoanalytics in die rapporteren op de server.
