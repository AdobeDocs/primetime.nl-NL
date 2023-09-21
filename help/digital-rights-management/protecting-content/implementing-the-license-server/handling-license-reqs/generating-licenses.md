---
title: Licenties genereren
description: Licenties genereren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Licenties genereren{#generating-licenses}

Als u een bladlicentie aan een gebruiker wilt geven, moet de SDK de CEK in de metagegevens van de inhoud decoderen en opnieuw coderen voor de computer die een licentie aanvraagt. Om CEK te decrypteren, moet de server informatie verstrekken die wordt vereist om de sleutel te decrypteren. Bellen `ContentInfo.setKeyRetrievalInfo()` en een `AsymmetricKeyRetrieval` object. Als de meta-gegevens veelvoudige beleid omvat, moet de server bepalen welk beleid te gebruiken en te roepen `LicenseRequestMessage.setSelectedPolicy()`. Dan roep `LicenseRequestMessage.generateLicense()` om de licentie te genereren. Met de `License` -object dat wordt geretourneerd, kunt u de vervaldatum of rechten in de licentie wijzigen.

Als een `ExternalKeyRetrieval` object wordt opgegeven in het dialoogvenster `ContentInfo` -object, dan wordt verwacht dat de licentieserver de bijbehorende CEK-id gebruikt om de juiste CEK op te halen die in de licentie is ingevoegd.

Zie de [Adobe Primetime DRM - extern CEK-overzicht](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md) voor meer informatie over het gebruik van de externe CEK-workflow.
