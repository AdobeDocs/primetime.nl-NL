---
description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
seo-description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
seo-title: Videoanalyse
title: Videoanalyse
uuid: c3cb0574-1117-409c-8aa7-641363d8d85f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Videoanalyse{#video-analytics}

U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.

Bij het bijhouden van video&#39;s in TVSDK wordt gebruik gemaakt van de service **Adobe Analytics Video Essentials** , die metrische gegevens over de videobetrokkenheid biedt, zoals videoweergaven, voltooide video en indrukkingen, de aan video bestede tijd, enzovoort. Neem voor meer informatie over deze service contact op met uw vertegenwoordiger van Adobe.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video volgende componenten:

   * **AppMeasurement-bibliotheek** - Bevat de kernlogica voor het verzamelen van gegevens op laag niveau. Dit is waar de videohartslaggegevens worden verzameld en over het netwerk verzonden.
   * **Videohartslagbibliotheek** - Bevat de kernlogica van de videohartslaggegevensverzameling. De videohartslagbibliotheek heeft toegang tot een subset van de API&#39;s van de `AppMeasurement` bibliotheek.

      >[!TIP]
      >
      >Uw app communiceert niet rechtstreeks met de videohartslagcode. In plaats daarvan gebruikt de app TVSDK API&#39;s om de mogelijkheden voor het bijhouden van video&#39;s van uw speler te configureren.

   * **BezoekerID-bibliotheek** : geeft bezoekers op unieke wijze aan op de webpagina waarop de videospeler wordt gehost.
   >[!IMPORTANT]
   >
   >De ingebouwde mogelijkheden voor videotracering voor TVSDK zijn afhankelijk van een correct geconfigureerde `AppMeasurement` instantie. De volgende elementen veronderstellen dat de `AppMeasurement` bibliotheek reeds wordt geconcretiseerd en alvorens video het volgen te vormen en te activeren. De mogelijkheden voor het bijhouden van TVSDK-video zijn afhankelijk van het bestaan van een volledig functioneel en correct geconfigureerd exemplaar van de `AppMeasurement` bibliotheek.

1. U kunt videoverslagen op de server instellen met Adobe Analytics Admin Tools.

