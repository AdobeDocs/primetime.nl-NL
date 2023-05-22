---
title: Licenties insluiten
description: Licenties insluiten
copied-description: true
exl-id: 8cd58808-73fb-4635-9a75-0520430f6b3a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Licenties insluiten {#embedding-licenses}

Nadat de inhoud is gecodeerd en er een licentie is gegenereerd, kan de licentie worden ingesloten in de gecodeerde inhoud.

Als u een licentie wilt insluiten, moet u een instantie van `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Als u het type van de gecodeerde inhoud kent, gebruik de aannemer voor `FLVKeyMetaDataUpdater` of `F4VKeyMetaDataUpdater`; anders gebruiken `MediaProcessorFactory.getMediaProcessor()` om een instantie te retourneren op basis van het gedetecteerde bestandstype. Vervolgens moet u een `KeyMetaDataCallback` en aanroepen `modifyKeyMetaData()`. Uw callback-implementatie wordt vervolgens aangeroepen wanneer de DRM-metagegevens zich in de gecodeerde inhoud bevinden. Op basis van de gevonden metagegevens kunt u een licentie kiezen om in te sluiten en de licentie in te stellen met `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Zie `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` in de opdrachtregelprogramma&#39;s voor de referentieimplementatie [!DNL Samples] map voor voorbeeldcode die ingesloten licenties demonstreert.

>[!NOTE]
>
>Een Adobe Primetime DRM 2.0-client negeert alle licenties die in de inhoud zijn ingesloten en probeert vervolgens een licentie te verkrijgen van de licentieserver die in de metagegevens is opgegeven. Als de metagegevens echter aangeven dat er geen licentieserver beschikbaar is, moet een Primetime DRM 2.0-client worden bijgewerkt voordat u de inhoud kunt weergeven.
