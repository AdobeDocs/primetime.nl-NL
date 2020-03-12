---
seo-title: Licenties genereren
title: Licenties genereren
uuid: f91b0cc8-e0ed-4722-947b-22eb2bfba916
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Licenties genereren{#generating-licenses}

Als u een bladlicentie aan een gebruiker wilt geven, moet de SDK de CEK in de metagegevens van de inhoud decoderen en opnieuw coderen voor de computer die een licentie aanvraagt. Om CEK te decrypteren, moet de server informatie verstrekken die wordt vereist om de sleutel te decrypteren. Roep een `ContentInfo.setKeyRetrievalInfo()` object aan `AsymmetricKeyRetrieval` en geef dit op. Als de meta-gegevens veelvoudige beleid omvat, moet de server bepalen welk beleid te gebruiken en te roepen `LicenseRequestMessage.setSelectedPolicy()`. Dan vraag `LicenseRequestMessage.generateLicense()` om de vergunning te produceren. Met het `License` object dat wordt geretourneerd, kunt u de vervaldatum of rechten in de licentie wijzigen.

Als een `ExternalKeyRetrieval` voorwerp in het `ContentInfo` voorwerp wordt gespecificeerd, dan wordt de vergunningsserver verwacht om bijbehorende CEK identiteitskaart te gebruiken om aangewezen CEK terug te winnen die in de vergunning wordt opgenomen.

Zie het externe CEK-overzicht [van](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md) Adobe Primetime DRM voor meer informatie over het gebruik van de externe CEK-workflow.
