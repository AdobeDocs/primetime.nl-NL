---
title: SWF-toepassing staat plaatsing toe
description: SWF-toepassing staat plaatsing toe
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# De toepassing van SWF staat lijst {#swf-application-allowlisting} toe

Als u een SWF-toepassing wilt lijsten van gewenste personen, kunt u een van de volgende twee strategieën volgen:

* U kunt een URL opgeven voor een SWF-bestand. Dit is een zeer flexibele benadering, vooral in een ontwikkelomgeving waarin u regelmatig uw SWF-bestand herbouwt.
* U kunt een SWF-HASH opgeven. Dit is een cryptografische samenvattingswaarde van uw SWF-bestand. Deze aanpak is minder flexibel (maar veel strenger), aangezien de SWF-HASH verandert wanneer de toepassing verandert en opnieuw wordt samengesteld. In deze situatie zal alle aan de vorige HASH gebonden inhoud niet op de nieuwe speler kunnen spelen en moeten worden herverpakt. Het [!DNL PolicyManager.jar] hulpmiddel zal automatisch de knoeiboel berekenen als u een [!DNL .swf] dossier specificeert.

   Anderzijds, als u Primetime DRM via Flash/Adobe Media Server (FMS/AMS) gebruikt, kunt u de weg aan uw bepaalde SWF(s) leveren, en FMS/AMS zal automatisch SWFs voor u verpakken in het DRM beleid dat wordt gebruikt om de inhoud te verpakken die door FMS/AMS wordt gestroomd.

Zie `policy.allowedSWFApplication.n` in *Configuration properties* voor meer informatie.
