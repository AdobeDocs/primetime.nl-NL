---
description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
seo-description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
seo-title: Integratie van videoanalysemogelijkheden
title: Integratie van videoanalysemogelijkheden
uuid: 275d2c88-a15c-4645-9234-f29d32fc4a63
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Integratie van videoanalysemogelijkheden {#video-analytics-integration}

U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.

Bij het bijhouden van video&#39;s in TVSDK wordt de service **Adobe Analytics Video Essentials** gebruikt. Deze service biedt meetgegevens voor videobetrokkenheid, zoals videoweergaven, voltooide video en indrukkingen, de tijd die aan video wordt besteed, enzovoort. Neem voor meer informatie over deze service contact op met uw Adobe-vertegenwoordiger.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video volgende componenten:

   Op iOS maken deze componenten deel uit van TVSDK:

   * JSON-configuratiebestand
   * Metagegevensobject voor videoanalyse
   * Algemeen metagegevensobject
   * Video analytics-trackerobject

1. Stel met Adobe Analytics Admin Tools videoanalytics in die rapporteren op de server.