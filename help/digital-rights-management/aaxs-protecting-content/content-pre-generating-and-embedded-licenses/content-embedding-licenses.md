---
seo-title: Licenties insluiten
title: Licenties insluiten
uuid: b8d8ee9b-7430-4899-9caf-47d6b64021b8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Licenties insluiten {#embedding-licenses}

Nadat de inhoud is gecodeerd en er een licentie is gegenereerd, kan de licentie worden ingesloten in de gecodeerde inhoud.

Als u een licentie wilt insluiten, vraagt u een exemplaar van `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. Als u het type van de gecodeerde inhoud kent, gebruik de aannemer voor `FLVKeyMetaDataUpdater` of `F4VKeyMetaDataUpdater`; anders, gebruik `MediaProcessorFactory.getMediaProcessor()` om een geval terug te keren dat op het ontdekte dossiertype wordt gebaseerd. Construeer een `KeyMetaDataCallback` en haal `modifyKeyMetaData()`. De callback-implementatie wordt geactiveerd wanneer de DRM-metagegevens zich in de gecodeerde inhoud bevinden. Op basis van de gevonden metagegevens kunt u een licentie kiezen om in te sluiten en de licentie in te stellen met `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

Zie `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` in de map Samples van de opdrachtregelprogramma&#39;s voor naslagimplementatie de voorbeeldcode voor het aantonen van ingesloten licenties.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Adobe Access 2.0-clients negeren alle licenties die in de inhoud zijn ingesloten en proberen een licentie te verkrijgen van de licentieserver die in de metagegevens is opgegeven. Als de metagegevens echter aangeven dat er geen licentieserver beschikbaar is, moet een Adobe Access 2.0-client een upgrade uitvoeren om de inhoud weer te geven.

Zie [out-of-band licenties](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
