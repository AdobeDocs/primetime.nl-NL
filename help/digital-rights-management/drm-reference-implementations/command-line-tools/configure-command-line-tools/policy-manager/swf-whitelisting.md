---
seo-title: Whitelisting van SWF-toepassing
title: Whitelisting van SWF-toepassing
uuid: e3021ae9-54f4-4bcf-a274-515ae765f74b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Whitelisting van SWF-toepassing{#swf-application-whitelisting}

Aan whitelist een Swf- toepassing, kunt u één van deze twee strategieën volgen:

* U kunt een URL opgeven voor een SWF-bestand. Dit is een zeer flexibele benadering, vooral in een ontwikkelomgeving waarin u regelmatig uw SWF-bestand herbouwt.
* U kunt een SWF-HASH opgeven. Dit is een cryptografische samenvattingswaarde van uw SWF-bestand. Deze aanpak is minder flexibel (maar veel strenger), aangezien de SWF-HASH verandert wanneer de toepassing verandert en opnieuw wordt samengesteld. In deze situatie zal alle aan de vorige HASH gebonden inhoud niet op de nieuwe speler kunnen spelen en moeten worden herverpakt. Het [!DNL PolicyManager.jar] gereedschap berekent automatisch de hash als u een [!DNL .swf] bestand opgeeft.

   Als u echter Primetime DRM gebruikt via Flash/Adobe Media Server (FMS/AMS), kunt u het pad naar uw specifieke SWF-bestanden opgeven. FMS/AMS zal de SWF-bestanden dan automatisch hashen zodat u deze kunt invoegen in het DRM-beleid dat wordt gebruikt om de inhoud te verpakken die door FMS/AMS wordt gestreamd.

Zie `policy.allowedSWFApplication.n` in de eigenschappen *van de* Configuratie voor details.
