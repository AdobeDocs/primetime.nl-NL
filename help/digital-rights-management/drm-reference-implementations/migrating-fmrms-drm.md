---
description: Als u licenties wilt blijven uitgeven voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moet u licentiegegevens en DRM-beleidsgegevens migreren van de LiveCycle ES-server naar de nieuwe server van de klant die is gebaseerd op de Adobe Primetime DRM SDK.
title: Migreren van FMRMS 1.0 of 1.5 naar Adobe Primetime DRM 2.0 of hoger
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Migreren van FMRMS 1.0 of 1.5 naar Adobe Primetime DRM 2.0 of hoger{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Als u licenties wilt blijven uitgeven voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moet u licentiegegevens en DRM-beleidsgegevens migreren van de LiveCycle ES-server naar de nieuwe server van de klant die is gebaseerd op de Adobe Primetime DRM SDK.

Voer de volgende taken uit om te migreren:

1. Informatie over de invoervergunning:

   1. Raadpleeg de voorbeelddatabasescripts in het dialoogvenster [!DNL Reference Implementation\Server\migration\db] map.
   1. Voer de steekproefmanuscripten in werking om relevante gegevens van een MySQL, een Oracle, of SQL gegevensbestand van de Server naar een Csv- dossierformaat uit te voeren.
   1. Nadat u de gegevens uit LiveCycle ES uitvoert, voer de gegevens in uw gegevensbestand in.

      De informatie over de geëxporteerde vergunning omvat het volgende:

      * Een licentie-id
      * A Content ID that assigned at packaging time
      * De id van het DRM-beleid dat wordt toegepast
      * De tijd waarop de inhoud is verpakt
      * De coderingssleutel voor inhoud

      Deze informatie is vereist voordat u de metagegevens voor 1.x-inhoud kunt converteren naar de DRM-metagegevensindeling voor primetime. In de verwijzingsimplementatie, wordt dit gegeven opgeslagen in de het gegevensbestandlijst van de Vergunning en gebruikt door `RefImplMetadataConvReqHandler`. Zie voor meer informatie `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler`.

1. FMRMS-beleid converteren naar de Primetime DRM-indeling:

   1. Voordat u het DRM-beleid kunt toepassen om metagegevens te converteren en licenties voor versie 1.0- of versie 1.5-inhoud te verlenen, moet u het bestaande DRM-beleid omzetten in de Primetime DRM-indeling.

      De `Reference Implementation\Server\migration` Deze map bevat voorbeeldcode voor het maken van een Primetime DRM-beleid dat is gebaseerd op ouder DRM-beleid. Als u wilt migreren van FMRMS 1.0 naar Primetime DRM, raadpleegt u de `V1_0PolicyConverter.java` monster nemen.
   1. De voorbeeldcode compileren door deze uit te voeren `ant-f build-migration.xml build-1.0-converter` -script, dat zoekt naar de 1.0- en Primetime DRM-bibliotheken in het dialoogvenster [!DNL libs/1.0] en [!DNL libs/flashaccess] mappen.

   1. Bewerk de [!DNL converter.properties] bestand dat naar uw LiveCycle ES-server verwijst.
   1. Uitvoeren `ant -f build-migration.xml migrate-all-1.0-policies` om alle FMRMS 1.0 DRM-beleidsregels om te zetten in de indeling Primetime DRM.

      Als u van FMRMS 1.5 naar Primetime DRM wilt migreren, raadpleegt u de `V1_5PolicyConverter.java` monster nemen.

   1. De voorbeeldcode compileren door deze uit te voeren `ant-f build-migration.xml build-1.5-converter` script, dat verwacht dat de 1.5- en 3.0-bibliotheken zich in de [!DNL libs/1.5] en [!DNL libs/flashaccess] mappen.

   1. Bewerk de [!DNL converter.properties] bestand dat naar uw LiveCycle ES-server verwijst.
   1. Uitvoeren `ant -f build-migration.xml migrate-all-1.5-policies` om alle FMRMS 1.5 DRM-beleidsregels om te zetten in Primetime DRM-indeling.

      Het omgezette DRM-beleid wordt opgeslagen als een set bestanden. De `DRM PolicyConverter` Hiermee wordt een CSV-bestand gegenereerd dat de toewijzing van de oude DRM-beleids-id&#39;s aan de nieuwe DRM-beleids-id&#39;s bevat. U kunt dit bestand importeren in de [!DNL PolicyConversion] tabel in de referentie-implementatiedatabank, waar deze wordt gebruikt door `RefImplMetadataConvReqHandler`.

1. De 1.x-compatibiliteitsaanvragen ondersteunen met de `FMRMSv1RequestHandler` en `FMRMSv1MetadataHandler` eigenschappen:

   1. Nadat de relevante gegevens zijn gemigreerd naar een DRM-gebaseerde Primetime-server, implementeert u ondersteuning voor 1.x-compatibiliteitsverzoeken.

      Voor voorbeelden over hoe te om deze types van verzoeken te verwerken, zie `RefImplUpgradeV1ClientHandler` en `RefImplMetadataConvReqHandler` in de referentieuitvoering.
