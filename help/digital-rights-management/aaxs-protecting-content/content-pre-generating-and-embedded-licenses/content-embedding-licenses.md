---
title: Licenties insluiten
description: Licenties insluiten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Licenties insluiten {#embedding-licenses}

Nadat de inhoud is gecodeerd en er een licentie is gegenereerd, kan de licentie worden ingesloten in de gecodeerde inhoud.

Als u een licentie wilt insluiten, ontvangt u een exemplaar van `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Als u het type van de gecodeerde inhoud kent, gebruik de aannemer voor `FLVKeyMetaDataUpdater` of `F4VKeyMetaDataUpdater`anders, gebruik `MediaProcessorFactory.getMediaProcessor()` om een instantie te retourneren op basis van het gedetecteerde bestandstype. Een `KeyMetaDataCallback` en aanroepen `modifyKeyMetaData()`. De callback-implementatie wordt geactiveerd wanneer de DRM-metagegevens zich in de gecodeerde inhoud bevinden. Op basis van de gevonden metagegevens kunt u een licentie kiezen om in te sluiten en de licentie in te stellen met `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Zie voor voorbeeldcode met ingesloten licenties `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` in de map &quot;Samples&quot; in de opdrachtregelprogramma&#39;s van de Reference Implementation.

>[!NOTE]
>
>Adobe Access 2.0-clients negeren alle licenties die in de inhoud zijn ingesloten en proberen een licentie te verkrijgen van de licentieserver die in de metagegevens is opgegeven. Nochtans, als de meta-gegevens erop wijzen dat geen vergunningsserver beschikbaar is, zal een cliënt van de Toegang 2.0 van de Adobe moeten bevorderen om de inhoud te bekijken.

Zie [Out-of-band licenties](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
