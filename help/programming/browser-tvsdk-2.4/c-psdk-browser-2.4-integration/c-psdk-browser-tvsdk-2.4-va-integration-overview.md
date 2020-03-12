---
description: U kunt het videogebruik bijhouden door Browser TVSDK te integreren met Adobe Analytics.
seo-description: U kunt het videogebruik bijhouden door Browser TVSDK te integreren met Adobe Analytics.
seo-title: Videoanalyse
title: Videoanalyse
uuid: 6351933b-c0f3-4e3e-ad27-bedc8eecc312
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Videoanalyse{#video-analytics}

U kunt het videogebruik bijhouden door Browser TVSDK te integreren met Adobe Analytics.

Bij het bijhouden van video&#39;s in Browser-TVSDK wordt gebruik gemaakt van de service **Adobe Analytics Video Essentials** , die metriek voor videobetrokkenheid biedt, zoals videoweergaven, voltooide video en indrukkingen, de tijd die aan video wordt besteed, enzovoort. Neem voor meer informatie over deze service contact op met uw vertegenwoordiger van Adobe.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video volgende componenten:

   * **AppMeasurement-bibliotheek** - Bevat de kernlogica voor het verzamelen van gegevens op laag niveau. Dit is waar de videohartslaggegevens worden verzameld en over het netwerk verzonden.
   * **Videohartslagbibliotheek** - Bevat de kernlogica van de videohartslaggegevensverzameling. De videohartslagbibliotheek heeft toegang tot een subset van de API&#39;s van de AppMeasurement-bibliotheek.

      >[!TIP]
      >
      >Uw app communiceert niet rechtstreeks met de videohartslagcode. In plaats daarvan gebruikt de app TVSDK-API&#39;s van de browser om de mogelijkheden voor het bijhouden van video&#39;s van uw speler te configureren.

   * **BezoekerID-bibliotheek** : geeft bezoekers op unieke wijze aan op de webpagina waarop de videospeler wordt gehost.
   >[!IMPORTANT]
   >
   >De ingebouwde mogelijkheid voor videotracering van de Browser-TVSDK is afhankelijk van een correct geconfigureerde AppMeasurement-instantie. De volgende elementen veronderstellen dat de bibliotheek AppMeasurement reeds wordt geconcretiseerd en gevormd alvorens video het volgen te vormen en te activeren. De mogelijkheden voor het bijhouden van video&#39;s van TVSDK van de browser zijn afhankelijk van het bestaan van een volledig functionele en correct geconfigureerde instantie van de AppMeasurement-bibliotheek.

1. U kunt videoverslagen op de server instellen met Adobe Analytics Admin Tools.