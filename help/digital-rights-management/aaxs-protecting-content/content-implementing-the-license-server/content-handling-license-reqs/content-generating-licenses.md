---
seo-title: Licenties genereren
title: Licenties genereren
uuid: 242d5567-f609-4781-a8a6-2f3d78471344
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Licenties genereren {#generating-licenses}

Als u een bladlicentie aan de gebruiker wilt geven, moet de SDK de CEK in de metagegevens van de inhoud decoderen en opnieuw coderen voor de computer die een licentie aanvraagt. Om CEK te decrypteren, moet de server informatie verstrekken die wordt vereist om de sleutel te decrypteren. Roep een `ContentInfo.setKeyRetrievalInfo()` object aan `AsymmetricKeyRetrieval` en geef dit op. Als de meta-gegevens veelvoudige beleid bevatten, moet de server bepalen welk beleid te gebruiken en te roepen `LicenseRequestMessage.setSelectedPolicy()`. Dan vraag `LicenseRequestMessage.generateLicense()` om de vergunning te produceren. Met het `License` object dat wordt geretourneerd, kunt u de vervaldatum of rechten in de licentie wijzigen.

Als een object ExternalKeyRetrieval in het `ContentInfo` object is opgegeven, wordt van de licentieserver verwacht dat deze de bijbehorende CEK-id gebruikt om de juiste CEK op te halen die in de licentie wordt ingevoegd. Zie [Adobe Access DRM External CEK Overview voor meer informatie over het gebruik van de externe CEK-workflow.](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
