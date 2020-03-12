---
description: Het belangrijkste client-side element van het DRM-systeem (Primetime Digital Rights Management) is DRM Manager.
seo-description: Het belangrijkste client-side element van het DRM-systeem (Primetime Digital Rights Management) is DRM Manager.
seo-title: Overzicht van de primaire DRM-interface
title: Overzicht van de primaire DRM-interface
uuid: 01714ee6-a937-4ca3-b535-6a6ef681ee6d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Overzicht van de primaire DRM-interface{#primetime-drm-interface-overview}

Het belangrijkste client-side element van het DRM-systeem (Primetime Digital Rights Management) is DRM Manager.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM biedt een schaalbare, efficiënte workflow voor het implementeren van inhoudsbeveiliging in TVSDK-toepassingen. U beschermt en beheert de rechten voor uw video-inhoud door een licentie te maken voor elk digitaal mediabestand.

TVSDK ondersteunt de integratie van Primetime DRM als aangepaste DRM-workflows. Dit betekent dat uw toepassing de DRM-verificatieworkflows moet implementeren voordat de stream kan worden afgespeeld met behulp van de Flash `DRMManager`. Om dit in te schakelen, `MediaPlayer` voorziet de manager van DRM u voor authentificatie.

Dit zijn de belangrijkste API-elementen voor het werken met DRM:

* Een verwijzing in de mediaspeler naar het DRM-beheerobject dat het DRM-subsysteem implementeert:

   ```
   public function get drmManager():DRMManager 
   ```

<!--<a id="section_4204CE2731A44F67A3664AEDE8CCCA47"></a>-->

Aanvullende relevante API-elementen:

* [flash.net.drm.DRMManager](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html)
* [flash.net.drm.DRMContentData](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMContentData.html)
* [flash.net.drm.DRMVoucher](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMVoucher.html)
* [flash.net.drm.AuthenticationMethod](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/AuthenticationMethod.html)
* [flash.events.DRMStatusEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMStatusEvent.html)
* [flash.events.DRMErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMErrorEvent.html)

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Raadpleeg de documentatie bij Adobe Primetime DRM voor meer informatie over DRM.
