---
seo-title: Migratie van FMRMS 1.0 of 1.5 naar Adobe Access 2.0 en hoger
title: Migratie van FMRMS 1.0 of 1.5 naar Adobe Access 2.0 en hoger
uuid: 05caeb39-0c62-4053-87a9-8e89030a188d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---


# Migreren van FMRMS 1.0 of 1.5 naar Adobe Access 2.0 en hoger {#migrating-from-fmrms-or-to-adobe-access-and-above}

Om licenties te blijven verlenen voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moeten licentie- en beleidsgegevens worden gemigreerd van de LiveCycle ES-server naar de nieuwe server van de klant op basis van de Adobe Access SDK. De belangrijkste stappen zijn:

1. Licentiegegevens importeren
1. FMRMS-beleid converteren naar Adobe Access-indeling
1. Ondersteuning voor de 1.x-compatibiliteitsaanvragen via `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler`

Als u licentiegegevens van LiveCycle ES wilt importeren in uw op Adobe Access gebaseerde server, raadpleegt u de voorbeelddatabasescripts in de map [!DNL Reference Implementation\Server\migration\db]. De manuscripten van de steekproef worden verstrekt voor het uitvoeren van de relevante gegevens van een MySQL, Oracle, of SQL gegevensbestand van de Server in een Csv- dossierformaat. Zodra de gegevens worden uitgevoerd, kan het in het gegevensbestand van uw keus worden ingevoerd. De geëxporteerde licentiegegevens omvatten de licentie-id, een inhoud-id die tijdens het verpakken is toegewezen, de id van het gebruikte beleid, de tijd waarop de inhoud is verpakt en de coderingssleutel voor de inhoud. Voor Adobe Access is deze informatie vereist om de metagegevens voor 1.x-inhoud om te zetten in de indeling voor Adobe Access-metagegevens (zie `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler`). In de verwijzingsimplementatie, wordt dit gegeven opgeslagen in de de gegevensbestandlijst van de Vergunning en gebruikt door `RefImplMetadataConvReqHandler`.

Het bestaande beleid zal in het formaat van de Toegang van de Adobe moeten worden omgezet om dat beleid te gebruiken wanneer het omzetten van meta-gegevens en het uitgeven van vergunningen voor 1.0 of 1.5 inhoud. The Reference Implementation\Server\migration folder contains sample code for creating an Adobe Access policy based on older policies.

Als u van FMRMS 1.0 aan de Toegang van Adobe migreert, zie de V1_0PolicyConverter.java steekproef. Compileer de steekproefcode door &quot; `ant-f build-migration.xml build-1.0-converter`&quot;in werking te stellen (het manuscript verwacht dat de 1.0 en bibliotheken van de Toegang van de Adobe in [!DNL libs/1.0] en libs/flashaccess respectievelijk zijn). Bewerk het bestand converter.properties om naar uw LiveCycle ES-server te wijzen. Voer vervolgens &quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot; uit om alle FMRMS 1.0-beleidsregels om te zetten in de indeling Adobe Access.

Als u van FMRMS 1.5 aan de Toegang van Adobe migreert, zie de V1_5PolicyConverter.java steekproef. Compileer de steekproefcode door &quot; `ant-f build-migration.xml build-1.5-converter`&quot;in werking te stellen (het manuscript verwacht dat de 1.5 en 3.0 bibliotheken in libs/1.5 en libs/flashaccess respectievelijk zijn). Bewerk het bestand converter.properties om naar uw LiveCycle ES-server te wijzen. Voer vervolgens &quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot; uit om alle FMRMS 1.5-beleidsregels om te zetten in de indeling Adobe Access.

Het omgezette beleid wordt naar een set bestanden geschreven. Bovendien zal PolicyConverter een Csv- dossier uitvoeren dat de afbeelding van oude beleid IDs aan nieuwe beleid IDs bevat. Dit dossier kan in de lijst &quot;PolicyConversion&quot;in het gegevensbestand van de verwijzingsImplementatie worden ingevoerd, en zal door `RefImplMetadataConvReqHandler` worden gebruikt.

Zodra de relevante gegevens zijn gemigreerd naar uw op Adobe Access gebaseerde server, bent u klaar om steun voor 1.x verenigbaarheidsverzoeken uit te voeren. Zie `RefImplUpgradeV1ClientHandler` en `RefImplMetadataConvReqHandler` in de verwijzingsimplementatie voor voorbeelden van hoe te om deze types van verzoeken te verwerken.
