---
seo-title: DRM-beleid bijwerken
title: DRM-beleid bijwerken
uuid: 6f7a1432-88e4-499b-a008-6c8cf0e9c09b
translation-type: tm+mt
source-git-commit: d5986e9bc8689bf37abdf242a41aea5e768df754

---


# DRM-beleid bijwerken {#updating-drm-policies}

Als het DRM-beleid wordt bijgewerkt nadat de inhoud is verpakt, geeft u het bijgewerkte DRM-beleid door aan de licentieserver, zodat de bijgewerkte versie kan worden gebruikt bij het uitgeven van een licentie. Als een licentieserver toegang heeft tot een database voor het opslaan van DRM-beleid, kunt u het bijgewerkte DRM-beleid ophalen uit de database en aanroepen `LicenseRequestMessage.setSelectedPolicy()` om de nieuwe versie van het DRM-beleid op te geven.

Voor vergunningsservers die niet op een centrale gegevensbestand vertrouwen, verleent SDK steun voor de Lijsten van de Update van het Beleid DRM. Een lijst met DRM-beleidsupdates is een bestand met een lijst met bijgewerkte of ingetrokken DRM-beleidsregels. Wanneer een beleid DRM wordt bijgewerkt, produceer een nieuwe Lijst van de Update van het Beleid DRM en duw periodiek de lijst aan alle vergunningsservers. Geef de lijst door aan SDK door te plaatsen `HandlerConfiguration.setPolicyUpdateList()`. Als er een updatelijst is opgegeven, raadpleegt de SDK deze lijst wanneer de metagegevens van de inhoud worden geparseerd. `ContentInfo.getUpdatedPolicies()` bevat de bijgewerkte versies van het DRM-beleid die in de metagegevens zijn opgegeven.

Zie [Werken met DRM-beleidsregels](../../../protecting-content/working-policies-overview/working-with-policies.md) en [DRM-beleidsupdate-lijsten](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)