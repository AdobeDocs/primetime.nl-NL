---
title: Licenties insluiten
description: Licenties insluiten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Licenties {#embedding-licenses} insluiten

Nadat de inhoud is gecodeerd en er een licentie is gegenereerd, kan de licentie worden ingesloten in de gecodeerde inhoud.

Als u een licentie wilt insluiten, verkrijgt u een exemplaar van `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Als u het type van de gecodeerde inhoud kent, gebruik de aannemer voor `FLVKeyMetaDataUpdater` of `F4VKeyMetaDataUpdater`; anders, gebruik `MediaProcessorFactory.getMediaProcessor()` om een instantie terug te keren die op het ontdekte dossiertype wordt gebaseerd. Construeer een `KeyMetaDataCallback` en roep `modifyKeyMetaData()` aan. De callback-implementatie wordt geactiveerd wanneer de DRM-metagegevens zich in de gecodeerde inhoud bevinden. Op basis van de gevonden metagegevens kunt u een licentie kiezen om de licentie in te sluiten en in te stellen met `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Zie `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` in de map Samples van de opdrachtregelprogramma&#39;s voor naslagimplementatie &quot;Samples&quot; voor voorbeeldcode die ingesloten licenties aantoont.

>[!NOTE]
>
>Adobe Access 2.0-clients negeren alle licenties die in de inhoud zijn ingesloten en proberen een licentie te verkrijgen van de licentieserver die in de metagegevens is opgegeven. Nochtans, als de meta-gegevens erop wijzen dat geen vergunningsserver beschikbaar is, zal een cliënt van de Toegang 2.0 van Adobe moeten bevorderen om de inhoud te bekijken.

Zie [Out-of-band licenties](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
