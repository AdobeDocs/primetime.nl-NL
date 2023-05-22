---
title: DRM-beleid bijwerken
description: DRM-beleid bijwerken
copied-description: true
exl-id: 27dc35d2-134c-4b88-9251-c6bb04a48f13
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# DRM-beleid bijwerken {#updating-drm-policies}

Als het DRM-beleid wordt bijgewerkt nadat de inhoud is verpakt, geeft u het bijgewerkte DRM-beleid door aan de licentieserver, zodat de bijgewerkte versie kan worden gebruikt bij het uitgeven van een licentie. Als een licentieserver toegang heeft tot een database voor het opslaan van DRM-beleid, kunt u het bijgewerkte DRM-beleid ophalen uit de database en bellen `LicenseRequestMessage.setSelectedPolicy()` om de nieuwe versie van het beleid te verstrekken DRM.

Voor vergunningsservers die niet op een centrale gegevensbestand vertrouwen, verleent SDK steun voor de Lijsten van de Update van het Beleid DRM. Een lijst met DRM-beleidsupdates is een bestand met een lijst met bijgewerkte of ingetrokken DRM-beleidsregels. Wanneer een beleid DRM wordt bijgewerkt, produceer een nieuwe Lijst van de Update van het Beleid DRM en duw periodiek de lijst aan alle vergunningsservers. Geef de lijst door aan de SDK door `HandlerConfiguration.setPolicyUpdateList()`. Als er een updatelijst is opgegeven, raadpleegt de SDK deze lijst wanneer de metagegevens van de inhoud worden geparseerd. `ContentInfo.getUpdatedPolicies()` bevat de bijgewerkte versies van het DRM-beleid die in de metagegevens zijn opgegeven.

Zie [Werken met DRM-beleid](../../../protecting-content/working-policies-overview/working-with-policies.md) en [Update-lijsten voor DRM-beleid](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
