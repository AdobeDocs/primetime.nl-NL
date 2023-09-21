---
title: Beleid bijwerken
description: Beleid bijwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Beleid bijwerken {#updating-policies}

Als het beleid wordt bijgewerkt nadat de inhoud is verpakt, geeft u het bijgewerkte beleid door aan de licentieserver, zodat de bijgewerkte versie kan worden gebruikt bij het uitgeven van een licentie. Als uw licentieserver toegang heeft tot een database voor het opslaan van beleidsregels, kunt u het bijgewerkte beleid ophalen uit de database en bellen `LicenseRequestMessage.setSelectedPolicy()` om de nieuwe versie van het beleid te verstrekken.

Voor vergunningsservers die niet op een centraal gegevensbestand vertrouwen, verleent SDK steun voor de Lijsten van de Update van het Beleid. Een lijst met beleidsupdates is een bestand met een lijst met bijgewerkte of ingetrokken beleidsregels. Wanneer een beleid wordt bijgewerkt, produceer een nieuwe Lijst van de Update van het Beleid en duw periodiek de lijst uit aan alle vergunningsservers. Geef de lijst door aan de SDK door `HandlerConfiguration.setPolicyUpdateList()`. Als er een updatelijst is opgegeven, raadpleegt de SDK deze lijst bij het parseren van de metagegevens van de inhoud. `ContentInfo.getUpdatedPolicies()` bevat de bijgewerkte versies van beleidsregels die in de metagegevens zijn opgegeven.

Zie [Werken met beleid](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) en [Lijst met beleidsupdates.](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
