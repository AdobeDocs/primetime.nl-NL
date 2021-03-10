---
title: Licenties insluiten
description: Licenties insluiten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Licenties {#embedding-licenses} insluiten

Nadat de inhoud is gecodeerd en er een licentie is gegenereerd, kan de licentie worden ingesloten in de gecodeerde inhoud.

Als u een licentie wilt insluiten, moet u een instantie van `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater` verkrijgen. Als u het type van de gecodeerde inhoud kent, gebruik de aannemer voor `FLVKeyMetaDataUpdater` of `F4VKeyMetaDataUpdater`; anders, gebruik `MediaProcessorFactory.getMediaProcessor()` om een instantie terug te keren die op het ontdekte dossiertype wordt gebaseerd. Vervolgens moet u een `KeyMetaDataCallback` maken en `modifyKeyMetaData()` aanroepen. Uw callback-implementatie wordt vervolgens aangeroepen wanneer de DRM-metagegevens zich in de gecodeerde inhoud bevinden. Op basis van de gevonden metagegevens kunt u een licentie kiezen om de licentie in te sluiten en in te stellen met `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Zie `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` in de folder van de Hulpmiddelen [!DNL Samples] van de Lijn van het Bevel van de Implementatie van de Verwijzing voor steekproefcode die ingebedde vergunningen aantoont.

>[!NOTE]
>
>Een Adobe Primetime DRM 2.0-client negeert alle licenties die in de inhoud zijn ingesloten en probeert vervolgens een licentie te verkrijgen van de licentieserver die in de metagegevens is opgegeven. Als de metagegevens echter aangeven dat er geen licentieserver beschikbaar is, moet een Primetime DRM 2.0-client worden bijgewerkt voordat u de inhoud kunt weergeven.

