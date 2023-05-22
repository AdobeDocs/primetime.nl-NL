---
description: Het belangrijkste client-side element van het DRM-systeem (Primetime Digital Rights Management) is DRM Manager.
title: Overzicht van de primaire DRM-interface
exl-id: 8d6b9416-5d8a-4d1e-b8e6-47c43389f079
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Overzicht van de primaire DRM-interface{#primetime-drm-interface-overview}

Het belangrijkste client-side element van het DRM-systeem (Primetime Digital Rights Management) is DRM Manager.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM biedt een schaalbare, efficiënte workflow voor het implementeren van inhoudsbeveiliging in TVSDK-toepassingen. U beschermt en beheert de rechten voor uw video-inhoud door een licentie te maken voor elk digitaal mediabestand.

TVSDK ondersteunt de integratie van Primetime DRM als aangepaste DRM-workflows. Dit betekent dat uw toepassing de DRM-verificatieworkflows moet implementeren voordat de stream kan worden afgespeeld met de Flash `DRMManager`. Om dit mogelijk te maken, `MediaPlayer` biedt u de DRM-manager voor verificatie.

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

Raadpleeg de Adobe Primetime DRM-documentatie voor meer informatie over DRM.
