---
title: Aanbieding toestaan in SWF-toepassing
description: Aanbieding toestaan in SWF-toepassing
copied-description: true
exl-id: ae8b7f52-897f-43f9-ac7b-665d4b8c16b8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Aanbieding toestaan in SWF-toepassing {#swf-application-allowlisting}

Om een toepassing van de SWF te lijsten van gewenste personen, kunt u één van deze twee strategieën volgen:

* U kunt een URL opgeven voor een SWF. Dit is een zeer flexibele benadering, vooral in een ontwikkelomgeving waarin u regelmatig uw SWF herbouwt.
* U kunt een SWF-HASH opgeven. Dit is een cryptografische samenvattingswaarde van uw SWF. Deze benadering is minder flexibel (maar veel strikter), aangezien de HASH van de SWF zal veranderen wanneer de toepassing verandert en wordt herbouwd. In deze situatie zal alle aan de vorige HASH gebonden inhoud niet op de nieuwe speler kunnen spelen en moeten worden herverpakt. De [!DNL PolicyManager.jar] wordt de hash automatisch berekend als u een [!DNL .swf] bestand.

   Anderzijds, als u Primetime DRM via Flash/Adobe Media Server (FMS/AMS) gebruikt, kunt u de weg aan uw bepaalde SWF(n) leveren, en FMS/AMS zal automatisch SWF voor u verpakken in het DRM beleid dat wordt gebruikt om de inhoud te verpakken die door FMS/AMS wordt gestroomd.

Zie `policy.allowedSWFApplication.n` in *Configuratieeigenschappen* voor meer informatie.
