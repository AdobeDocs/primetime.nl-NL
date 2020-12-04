---
seo-title: Beleid bijwerken
title: Beleid bijwerken
uuid: f6686c8b-bedf-4ec5-a14e-f03326519f89
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Beleid {#updating-policies} bijwerken

Als het beleid wordt bijgewerkt nadat de inhoud is verpakt, geeft u het bijgewerkte beleid door aan de licentieserver, zodat de bijgewerkte versie kan worden gebruikt bij het uitgeven van een licentie. Als uw licentieserver toegang heeft tot een database voor het opslaan van beleid, kunt u het bijgewerkte beleid ophalen uit de database en `LicenseRequestMessage.setSelectedPolicy()` aanroepen om de nieuwe versie van het beleid op te geven.

Voor vergunningsservers die niet op een centraal gegevensbestand vertrouwen, verleent SDK steun voor de Lijsten van de Update van het Beleid. Een lijst met beleidsupdates is een bestand met een lijst met bijgewerkte of ingetrokken beleidsregels. Wanneer een beleid wordt bijgewerkt, produceer een nieuwe Lijst van de Update van het Beleid en duw periodiek de lijst uit aan alle vergunningsservers. Geef de lijst door aan SDK door `HandlerConfiguration.setPolicyUpdateList()` te plaatsen. Als er een updatelijst is opgegeven, raadpleegt de SDK deze lijst bij het parseren van de metagegevens van de inhoud. `ContentInfo.getUpdatedPolicies()` bevat de bijgewerkte versies van beleidsregels die in de metagegevens zijn opgegeven.

Zie [Werken met beleidsregels](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) en [Beleidsupdate-lijsten.](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
