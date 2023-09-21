---
description: U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.
title: Integratie van videoanalysemogelijkheden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Integratie van videoanalysemogelijkheden {#video-analytics-integration}

U kunt het videogebruik bijhouden door TVSDK te integreren met Adobe Analytics.

Bij het bijhouden van video&#39;s in TVSDK wordt het **Adobe Analytics Video Essentials** service, die metriek voor videobetrokkenheid biedt, zoals videoweergaven, voltooide video en indrukken, tijd die aan video wordt besteed, enzovoort. Neem voor meer informatie over deze service contact op met uw Adobe.

In de volgende procedure worden de stappen beschreven waarmee videotracering in de speler wordt geactiveerd:

1. Initialiseer en/of vorm de volgende video het volgen componenten:

   In iOS maken deze componenten deel uit van TVSDK:

   * JSON-configuratiebestand
   * Metagegevensobject voor videoanalyse
   * Algemeen metagegevensobject
   * Video analytics-trackerobject

1. Stel met Adobe Analytics Admin Tools videoanalytics in die rapporteren op de server.
