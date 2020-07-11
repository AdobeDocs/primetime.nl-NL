---
seo-title: SWF-toepassing staat plaatsing toe
title: SWF-toepassing staat plaatsing toe
uuid: e3021ae9-54f4-4bcf-a274-515ae765f74b
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# SWF-toepassing staat plaatsing toe {#swf-application-allowlisting}

Als u een SWF-toepassing wilt lijsten van gewenste personen, kunt u een van de volgende twee strategieën volgen:

* U kunt een URL opgeven voor een SWF-bestand. Dit is een zeer flexibele benadering, vooral in een ontwikkelomgeving waarin u regelmatig uw SWF-bestand herbouwt.
* U kunt een SWF-HASH opgeven. Dit is een cryptografische samenvattingswaarde van uw SWF-bestand. Deze aanpak is minder flexibel (maar veel strenger), aangezien de SWF-HASH verandert wanneer de toepassing verandert en opnieuw wordt samengesteld. In deze situatie zal alle aan de vorige HASH gebonden inhoud niet op de nieuwe speler kunnen spelen en moeten worden herverpakt. Het [!DNL PolicyManager.jar] gereedschap berekent automatisch de hash als u een [!DNL .swf] bestand opgeeft.

   Als u echter Primetime DRM gebruikt via Flash/Adobe Media Server (FMS/AMS), kunt u het pad naar uw specifieke SWF-bestanden opgeven. FMS/AMS zal de SWF-bestanden dan automatisch hashen zodat u deze kunt invoegen in het DRM-beleid dat wordt gebruikt om de inhoud te verpakken die door FMS/AMS wordt gestreamd.

Zie `policy.allowedSWFApplication.n` in de eigenschappen *van de* Configuratie voor details.
