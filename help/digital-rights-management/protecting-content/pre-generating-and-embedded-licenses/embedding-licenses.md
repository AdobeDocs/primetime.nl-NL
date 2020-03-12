---
seo-title: Licenties insluiten
title: Licenties insluiten
uuid: e3d55376-07de-479c-9a53-04bc8071ced4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Licenties insluiten {#embedding-licenses}

Nadat de inhoud is gecodeerd en er een licentie is gegenereerd, kan de licentie worden ingesloten in de gecodeerde inhoud.

Als u een licentie wilt insluiten, moet u een exemplaar van `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Als u het type van de gecodeerde inhoud kent, gebruik de aannemer voor `FLVKeyMetaDataUpdater` of `F4VKeyMetaDataUpdater`; anders, gebruik `MediaProcessorFactory.getMediaProcessor()` om een geval terug te keren dat op het ontdekte dossiertype wordt gebaseerd. Dan moet u een construeren `KeyMetaDataCallback` en aanhalen `modifyKeyMetaData()`. Uw callback-implementatie wordt vervolgens aangeroepen wanneer de DRM-metagegevens zich in de gecodeerde inhoud bevinden. Op basis van de gevonden metagegevens kunt u een licentie kiezen om in te sluiten en de licentie in te stellen met `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Zie `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` [!DNL Samples] in de map Reference Implementation Command Line Tools voor voorbeeldcode die ingesloten licenties aantoont.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Een Adobe Primetime DRM 2.0-client negeert alle licenties die in de inhoud zijn ingesloten en probeert vervolgens een licentie te verkrijgen van de licentieserver die in de metagegevens is opgegeven. Als de metagegevens echter aangeven dat er geen licentieserver beschikbaar is, moet een Primetime DRM 2.0-client worden bijgewerkt voordat u de inhoud kunt weergeven.

