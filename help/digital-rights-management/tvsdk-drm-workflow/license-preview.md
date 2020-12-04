---
seo-title: Voorvertoning van licentie
title: Voorvertoning van licentie
uuid: 61ff171f-b977-40ef-8e8d-2900316fa89a
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Voorvertoning van licentie {#license-preview}

Als er een vraag is of een apparaat een Primetime DRM-licentie kan gebruiken en volledig kan afdwingen, kunt u de functie Voorvertoning licentie gebruiken. Een voorbeeldlicentie komt volledig overeen met alle beperkingen en beperkingen die in de definitieve licentie zijn gedefinieerd, maar bevat niet de Content Encryption Key (CEK) die nodig is om de beveiligde inhoud te decoderen. Dit vermogen is nuttig om te bepalen of de cliënt inderdaad de vergunning kan verbruiken alvorens de Verdeler van de Inhoud een besluit neemt om een bepaalde vergunning aan de cliënt te verstrekken. Bijvoorbeeld - een klant wil HD-inhoud bekijken, maar de Content Distributor wil ervoor zorgen dat het apparaat HDCP volledig kan detecteren en inschakelen. In dit geval kan de client `DRMManager.loadPreviewVoucher()` aanroepen. Als een `DRMStatusEvent` in plaats van een `DRMErrorEvent` wordt ontvangen, wordt bevestigd dat de client de uitvoerbeveiligingsbeperkingen in de licentie volledig kan afdwingen en dat de Content Distributor dit type licentie vrijelijk aan de client kan leveren.

[iOS purchasePreviewLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android verwervingPreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
