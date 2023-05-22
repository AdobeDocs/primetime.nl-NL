---
title: Migratie van FMRMS 1.0 of 1.5 naar Adobe Access 2.0 en hoger
description: Migratie van FMRMS 1.0 of 1.5 naar Adobe Access 2.0 en hoger
copied-description: true
exl-id: 9aadf9a0-a7c5-466b-9dd1-c1bab2b8bfc6
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Migratie van FMRMS 1.0 of 1.5 naar Adobe Access 2.0 en hoger {#migrating-from-fmrms-or-to-adobe-access-and-above}

Om licenties te blijven verlenen voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moeten licentie- en beleidsgegevens worden gemigreerd van de LiveCycle ES-server naar de nieuwe server van de klant op basis van de Adobe Access SDK. De belangrijkste stappen zijn:

1. Licentiegegevens importeren
1. FMRMS-beleid converteren naar Adobe Access-indeling
1. De 1.x-compatibiliteitsverzoeken ondersteunen via de `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler`

Als u licentiegegevens van LiveCycle ES wilt importeren in uw op Adobe Access gebaseerde server, raadpleegt u de voorbeelddatabasescripts in het dialoogvenster [!DNL Reference Implementation\Server\migration\db] map. De manuscripten van de steekproef worden verstrekt voor het uitvoeren van de relevante gegevens van een MySQL, Oracle, of SQL gegevensbestand van de Server in een Csv- dossierformaat. Zodra de gegevens worden uitgevoerd, kan het in het gegevensbestand van uw keus worden ingevoerd. De geëxporteerde licentiegegevens omvatten de licentie-id, een inhoud-id die tijdens het verpakken is toegewezen, de id van het gebruikte beleid, de tijd waarop de inhoud is verpakt en de coderingssleutel voor de inhoud. Voor Adobe Access is deze informatie vereist om de metagegevens voor 1.x-inhoud te converteren naar de indeling voor Adobe Access-metagegevens (zie `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler`). In de verwijzingsimplementatie, worden dit gegeven opgeslagen in de het gegevensbestandlijst van de Vergunning en gebruikt door `RefImplMetadataConvReqHandler`.

Het bestaande beleid zal in het formaat van de Toegang van de Adobe moeten worden omgezet om dat beleid te gebruiken wanneer het omzetten van meta-gegevens en het uitgeven van vergunningen voor 1.0 of 1.5 inhoud. De de migratiemap van de Server \ van de Implementatie van de Verwijzing \ bevat steekproefcode voor het creëren van een beleid van de Toegang van de Adobe dat op ouder beleid wordt gebaseerd.

Als u van FMRMS 1.0 aan de Toegang van Adobe migreert, zie de V1_0PolicyConverter.java steekproef. De voorbeeldcode compileren door &quot; `ant-f build-migration.xml build-1.0-converter`&quot; (Het script verwacht dat de 1.0- en Adobe Access-bibliotheken zich in [!DNL libs/1.0] en libs/flashaccess). Bewerk het bestand converter.properties om naar uw LiveCycle ES-server te wijzen. Voer vervolgens &quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot; om alle FMRMS 1.0-beleidsregels om te zetten in de indeling Adobe Access.

Als u van FMRMS 1.5 aan de Toegang van Adobe migreert, zie de V1_5PolicyConverter.java steekproef. De voorbeeldcode compileren door &quot; `ant-f build-migration.xml build-1.5-converter`&quot; (Het script verwacht dat de 1.5- en 3.0-bibliotheken respectievelijk libs/1.5 en libs/flashaccess bevatten). Bewerk het bestand converter.properties om naar uw LiveCycle ES-server te wijzen. Voer vervolgens &quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot; om alle FMRMS 1.5-beleidsregels om te zetten in de indeling Adobe Access.

Het omgezette beleid wordt naar een set bestanden geschreven. Bovendien zal PolicyConverter een Csv- dossier uitvoeren dat de afbeelding van oude beleid IDs aan nieuwe beleid IDs bevat. Dit bestand kan worden geïmporteerd in de tabel &quot;PolicyConversion&quot; in de database voor de referentie-implementatie en wordt gebruikt door `RefImplMetadataConvReqHandler`.

Zodra de relevante gegevens zijn gemigreerd naar uw op Adobe Access gebaseerde server, bent u klaar om steun voor 1.x verenigbaarheidsverzoeken uit te voeren. Zie `RefImplUpgradeV1ClientHandler` en `RefImplMetadataConvReqHandler` in de referentieimplementatie voor voorbeelden van hoe te om deze types van verzoeken te verwerken.
