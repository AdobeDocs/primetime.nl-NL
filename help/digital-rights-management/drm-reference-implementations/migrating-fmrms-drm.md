---
description: Als u licenties wilt blijven uitgeven voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moet u licentiegegevens en DRM-beleidsgegevens migreren van de LiveCycle ES-server naar de nieuwe server van de klant die is gebaseerd op de Adobe Primetime DRM SDK.
seo-description: Als u licenties wilt blijven uitgeven voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moet u licentiegegevens en DRM-beleidsgegevens migreren van de LiveCycle ES-server naar de nieuwe server van de klant die is gebaseerd op de Adobe Primetime DRM SDK.
seo-title: Migreren van FMRMS 1.0 of 1.5 naar Adobe Primetime DRM 2.0 of hoger
title: Migreren van FMRMS 1.0 of 1.5 naar Adobe Primetime DRM 2.0 of hoger
uuid: 49ecbbd2-d83b-4bf2-841e-c3f9e5d5e141
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Migreren van FMRMS 1.0 of 1.5 naar Adobe Primetime DRM 2.0 of hoger{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Als u licenties wilt blijven uitgeven voor inhoud die is verpakt met Flash Media Rights Management Server (FMRMS) 1.0 of 1.5, moet u licentiegegevens en DRM-beleidsgegevens migreren van de LiveCycle ES-server naar de nieuwe server van de klant die is gebaseerd op de Adobe Primetime DRM SDK.

Voer de volgende taken uit om te migreren:

1. Informatie over de invoervergunning:

   1. Raadpleeg de voorbeelddatabasescripts in de [!DNL Reference Implementation\Server\migration\db] map voor informatie over het importeren van licentiegegevens van LiveCycle ES naar uw op Primetime DRM gebaseerde server.
   1. Voer de steekproefmanuscripten in werking om relevante gegevens van een MySQL, Oracle, of SQL gegevensbestand van de Server naar een Csv- dossierformaat uit te voeren.
   1. Nadat u de gegevens uit LiveCycle ES hebt geëxporteerd, importeert u de gegevens naar uw database.

      De informatie over de geëxporteerde vergunning omvat het volgende:

      * Een licentie-id
      * A Content ID that assigned at packaging time
      * De id van het DRM-beleid dat wordt toegepast
      * De tijd waarop de inhoud is verpakt
      * De coderingssleutel voor inhoud
      Deze informatie is vereist voordat u de metagegevens voor 1.x-inhoud kunt converteren naar de DRM-metagegevensindeling voor primetime. In de verwijzingsimplementatie, wordt dit gegeven opgeslagen in de het gegevensbestandlijst van de Vergunning en gebruikt door `RefImplMetadataConvReqHandler`. For more information, see `FMRMSv1RequestHandler` and `FMRMSv1MetadataHandler`.


1. FMRMS-beleid converteren naar de Primetime DRM-indeling:

   1. Voordat u het DRM-beleid kunt toepassen om metagegevens te converteren en licenties voor versie 1.0- of versie 1.5-inhoud te verlenen, moet u het bestaande DRM-beleid omzetten in de Primetime DRM-indeling.

      De `Reference Implementation\Server\migration` map bevat voorbeeldcode voor het maken van een Primetime DRM-beleid dat is gebaseerd op ouder DRM-beleid. Voor migratie van FMRMS 1.0 naar Primetime DRM, zie het `V1_0PolicyConverter.java` monster.
   1. Compileer de steekproefcode door `ant-f build-migration.xml build-1.0-converter` manuscript in werking te stellen, dat naar de 1.0 en bibliotheken van Primetime DRM in de [!DNL libs/1.0] en [!DNL libs/flashaccess] folders zoekt.

   1. Bewerk het [!DNL converter.properties] bestand om naar uw LiveCycle ES-server te wijzen.
   1. Uitvoeren `ant -f build-migration.xml migrate-all-1.0-policies` om alle FMRMS 1.0 DRM-beleidsregels om te zetten in de indeling Primetime DRM.

      Voor migratie van FMRMS 1.5 naar Primetime DRM, zie het `V1_5PolicyConverter.java` monster.

   1. Compileer de steekproefcode door `ant-f build-migration.xml build-1.5-converter` manuscript in werking te stellen, dat de 1.5 en 3.0 bibliotheken om in [!DNL libs/1.5] en [!DNL libs/flashaccess] folders verwacht te zijn.

   1. Bewerk het [!DNL converter.properties] bestand om naar uw LiveCycle ES-server te wijzen.
   1. Voer uit `ant -f build-migration.xml migrate-all-1.5-policies` om alle FMRMS 1.5 DRM-beleidsregels om te zetten in de indeling Primetime DRM.

      Het omgezette DRM-beleid wordt opgeslagen als een set bestanden. Het `DRM PolicyConverter` genereert een CSV-bestand dat de toewijzing van de oude DRM-beleids-id&#39;s aan de nieuwe DRM-beleids-id&#39;s bevat. U kunt dit bestand importeren naar de [!DNL PolicyConversion] tabel in de database van de referentie-implementatie, waar het wordt gebruikt door `RefImplMetadataConvReqHandler`.

1. De 1.x-compatibiliteitsaanvragen met de `FMRMSv1RequestHandler` eigenschappen en `FMRMSv1MetadataHandler` eigenschappen ondersteunen:

   1. Nadat de relevante gegevens zijn gemigreerd naar een DRM-gebaseerde Primetime-server, implementeert u ondersteuning voor 1.x-compatibiliteitsverzoeken.

      Voor voorbeelden over hoe te om deze types van verzoeken te verwerken, zie `RefImplUpgradeV1ClientHandler` en `RefImplMetadataConvReqHandler` in de verwijzingsimplementatie.

