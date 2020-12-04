---
description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
seo-description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
seo-title: Videoanalyse
title: Videoanalyse
uuid: c3cb0574-1117-409c-8aa7-641363d8d85f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Videoanalyse{#video-analytics}

U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.

Bij het bijhouden van video&#39;s in TVSDK wordt de service **Adobe Analytics Video Essentials** gebruikt. Deze service biedt meetgegevens voor videobetrokkenheid, zoals videoweergaven, voltooide video en indrukkingen, de tijd die aan video wordt besteed, enzovoort. Neem voor meer informatie over deze service contact op met uw Adobe-vertegenwoordiger.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video volgende componenten:

   * **AppMeasurement-bibliotheek** : bevat de kernlogica voor het verzamelen van gegevens op laag niveau. Dit is waar de videohartslaggegevens worden verzameld en over het netwerk verzonden.
   * **Videohartslagbibliotheek**  - Bevat de kernlogica van de videohartslaggegevensverzameling. De videohartslagbibliotheek heeft toegang tot een subset van de `AppMeasurement` bibliotheek-API&#39;s.

      >[!TIP]
      >
      >Uw app communiceert niet rechtstreeks met de videohartslagcode. In plaats daarvan gebruikt de app TVSDK API&#39;s om de mogelijkheden voor het bijhouden van video&#39;s van uw speler te configureren.

   * **BezoekerID-bibliotheek** : geeft bezoekers op unieke wijze aan op de webpagina waarop de videospeler wordt gehost.
   >[!IMPORTANT]
   >
   >De ingebouwde mogelijkheid voor het bijhouden van video&#39;s in TVSDK is afhankelijk van een correct geconfigureerde `AppMeasurement`-instantie. De volgende elementen veronderstellen dat de `AppMeasurement` bibliotheek reeds wordt geconcretiseerd en alvorens video het volgen te vormen en te activeren. De mogelijkheden voor het bijhouden van TVSDK-video zijn afhankelijk van het bestaan van een volledig functionele en correct geconfigureerde instantie van de `AppMeasurement`-bibliotheek.

1. Stel met Adobe Analytics Admin Tools videoanalytics in die rapporteren op de server.

