---
description: Als u licenties wilt blijven uitgeven voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moet u licentiegegevens en DRM-beleidsgegevens migreren van de LiveCycle ES-server naar de nieuwe server van de klant die is gebaseerd op de Adobe Primetime DRM SDK.
title: Migreren van FMRMS 1.0 of 1.5 naar Adobe Primetime DRM 2.0 of hoger
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---


# Migreren van FMRMS 1.0 of 1.5 naar Adobe Primetime DRM 2.0 of hoger{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Als u licenties wilt blijven uitgeven voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moet u licentiegegevens en DRM-beleidsgegevens migreren van de LiveCycle ES-server naar de nieuwe server van de klant die is gebaseerd op de Adobe Primetime DRM SDK.

Voer de volgende taken uit om te migreren:

1. Informatie over de invoervergunning:

   1. Raadpleeg de voorbeelddatabasescripts in de map [!DNL Reference Implementation\Server\migration\db] als u licentiegegevens van LiveCycle ES wilt importeren naar uw op Primetime DRM gebaseerde server.
   1. Voer de steekproefmanuscripten in werking om relevante gegevens van een MySQL, een Oracle, of SQL gegevensbestand van de Server naar een Csv- dossierformaat uit te voeren.
   1. Nadat u de gegevens uit LiveCycle ES hebt geëxporteerd, importeert u de gegevens naar uw database.

      De informatie over de geëxporteerde vergunning omvat het volgende:

      * Een licentie-id
      * A Content ID that assigned at packaging time
      * De id van het DRM-beleid dat wordt toegepast
      * De tijd waarop de inhoud is verpakt
      * De coderingssleutel voor inhoud

      Deze informatie is vereist voordat u de metagegevens voor 1.x-inhoud kunt converteren naar de DRM-metagegevensindeling voor primetime. In de verwijzingsimplementatie, wordt dit gegeven opgeslagen in de de gegevensbestandlijst van de Vergunning en door `RefImplMetadataConvReqHandler` gebruikt. Zie `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler` voor meer informatie.


1. FMRMS-beleid converteren naar de Primetime DRM-indeling:

   1. Voordat u het DRM-beleid kunt toepassen om metagegevens te converteren en licenties voor versie 1.0- of versie 1.5-inhoud te verlenen, moet u het bestaande DRM-beleid omzetten in de Primetime DRM-indeling.

      De map `Reference Implementation\Server\migration` bevat voorbeeldcode voor het maken van een Primetime DRM-beleid dat is gebaseerd op ouder DRM-beleid. Zie het `V1_0PolicyConverter.java`-voorbeeld voor migratie van FMRMS 1.0 naar Primetime DRM.
   1. Compileer de steekproefcode door `ant-f build-migration.xml build-1.0-converter` manuscript in werking te stellen, dat naar de 1.0 en bibliotheken van Primetime DRM in [!DNL libs/1.0] en [!DNL libs/flashaccess] folders zoekt.

   1. Bewerk het [!DNL converter.properties]-bestand om naar uw LiveCycle ES-server te verwijzen.
   1. Voer `ant -f build-migration.xml migrate-all-1.0-policies` uit om alle FMRMS 1.0 DRM-beleidsregels om te zetten in Primetime DRM-indeling.

      Zie het `V1_5PolicyConverter.java`-voorbeeld voor migratie van FMRMS 1.5 naar Primetime DRM.

   1. Compileer de steekproefcode door `ant-f build-migration.xml build-1.5-converter` manuscript in werking te stellen, dat de 1.5 en 3.0 bibliotheken om in [!DNL libs/1.5] en [!DNL libs/flashaccess] folders verwacht te zijn.

   1. Bewerk het [!DNL converter.properties]-bestand om naar uw LiveCycle ES-server te verwijzen.
   1. Voer `ant -f build-migration.xml migrate-all-1.5-policies` uit om alle FMRMS 1.5 DRM-beleidsregels om te zetten in Primetime DRM-indeling.

      Het omgezette DRM-beleid wordt opgeslagen als een set bestanden. `DRM PolicyConverter` produceert een CSV-Geformatteerd dossier dat de afbeelding van oude DRM beleids IDs aan nieuwe DRM beleid IDs omvat. U kunt dit bestand importeren naar de tabel [!DNL PolicyConversion] in de database van de referentie-implementatie, waar het wordt gebruikt door `RefImplMetadataConvReqHandler`.

1. Ondersteun de 1.x verenigbaarheidsverzoeken met `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler` eigenschappen:

   1. Nadat de relevante gegevens zijn gemigreerd naar een DRM-gebaseerde Primetime-server, implementeert u ondersteuning voor 1.x-compatibiliteitsverzoeken.

      Voor voorbeelden over hoe te om deze types van verzoeken te verwerken, zie `RefImplUpgradeV1ClientHandler` en `RefImplMetadataConvReqHandler` in de verwijzingsimplementatie.

