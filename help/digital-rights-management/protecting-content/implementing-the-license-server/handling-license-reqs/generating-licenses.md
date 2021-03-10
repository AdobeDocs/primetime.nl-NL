---
title: Licenties genereren
description: Licenties genereren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Licenties genereren{#generating-licenses}

Als u een bladlicentie aan een gebruiker wilt geven, moet de SDK de CEK in de metagegevens van de inhoud decoderen en opnieuw coderen voor de computer die een licentie aanvraagt. Om CEK te decrypteren, moet de server informatie verstrekken die wordt vereist om de sleutel te decrypteren. Roep `ContentInfo.setKeyRetrievalInfo()` aan en geef een `AsymmetricKeyRetrieval`-object op. Als de metagegevens meerdere beleidsregels bevatten, moet de server bepalen welk beleid moet worden gebruikt en aangeroepen `LicenseRequestMessage.setSelectedPolicy()`. Dan vraag `LicenseRequestMessage.generateLicense()` om de vergunning te produceren. Met behulp van het `License`-object dat wordt geretourneerd, kunt u de vervaldatum of rechten in de licentie wijzigen.

Als een `ExternalKeyRetrieval` voorwerp in `ContentInfo` voorwerp wordt gespecificeerd, dan wordt de vergunningsserver verwacht om bijbehorende CEK identiteitskaart te gebruiken om aangewezen CEK terug te winnen die in de vergunning wordt opgenomen.

Zie [Adobe Primetime DRM External CEK Overview](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md) voor meer informatie over het gebruik van de externe CEK-workflow.
