---
title: Licenties genereren
description: Licenties genereren
copied-description: true
exl-id: 65c5677d-5a69-46f8-bc14-7af6d14d4dff
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Licenties genereren {#generating-licenses}

Als u een bladlicentie aan de gebruiker wilt geven, moet de SDK de CEK in de metagegevens van de inhoud decoderen en opnieuw coderen voor de computer die een licentie aanvraagt. Om CEK te decrypteren, moet de server informatie verstrekken die wordt vereist om de sleutel te decrypteren. Bellen `ContentInfo.setKeyRetrievalInfo()` en een `AsymmetricKeyRetrieval` object. Als de meta-gegevens veelvoudige beleid bevatten, moet de server bepalen welk beleid te gebruiken en te roepen `LicenseRequestMessage.setSelectedPolicy()`. Dan roep `LicenseRequestMessage.generateLicense()` om de licentie te genereren. Met de `License` -object dat wordt geretourneerd, kunt u de vervaldatum of rechten in de licentie wijzigen.

Als een ExternalKeyRetrieval-object is opgegeven in het dialoogvenster `ContentInfo` -object, dan wordt verwacht dat de licentieserver de bijbehorende CEK-id gebruikt om de juiste CEK op te halen die in de licentie wordt ingevoegd. Ga voor meer informatie over het gebruik van de externe CEK-workflow naar [Adobe Access DRM - Overzicht externe CEK](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
