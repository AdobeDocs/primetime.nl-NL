---
seo-title: Compatibiliteit met Flash Media Rights Management Server 1.x garanderen
title: Compatibiliteit met Flash Media Rights Management Server 1.x garanderen
uuid: 0160ca02-ebe6-4090-bf32-1d1a46088844
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Compatibiliteit met Flash Media Rights Management Server 1.x{#ensure-compatibility-with-flash-media-rights-management-server-x} garanderen

Flash Media Rights Management Server 1.x en Adobe Access gebruiken verschillende metagegevens voor het verpakken van inhoud en het aanvragen van licenties. Voor Adobe Access om FMRMS versie 1.x-inhoud te kunnen gebruiken, moeten de metagegevens worden omgezet.

De Adobe Access SDK ondersteunt twee opties voor het omzetten van metagegevens:

* Off line (aanbevolen)

   Genereer de Adobe Access-metagegevens in een offlineproces en sla deze op voor gebruik wanneer een client hierom vraagt. Adobe raadt deze optie aan. Als de meta-gegevens off-line wordt geproduceerd, heeft de vergunningsserver geen toegang tot 1.x CEKs of de pakketreferentie nodig. Daarnaast biedt het omzetten van offline betere prestaties omdat de licentieserver de metagegevens niet in real-time hoeft te genereren.

* Op aanvraag

   Genereer de Adobe Access-metagegevens op aanvraag wanneer een client hierom vraagt. Wanneer een Adobe Access-client versie 1.x-inhoud downloadt, verzendt het de DRM-metagegevens (ook wel DRM-header genoemd) naar de Adobe Access SDK. De SDK converteert de DRM-metagegevens naar de huidige indeling. De SDK versleutelt en sluit de inhoudscoderingssleutel (CEK) in de metagegevens in en stuurt de inhoud terug naar de Adobe Access-client. (De Adobe Access 1.x-metagegevens bevatten niet de CEK.)

   Om de meta-gegevens om te zetten, vereist de Toegang van de Adobe toegang toegang tot de de encryptiesleutels van de Adobe Access 1.x inhoud. Wanneer u van de Server 1.x van het Rights Management van de Media van de Flash Media migreert, kunt u de sleutels van de inhoudsencryptie in het gegevensbestand blijven opslaan van LiveCycle ES, of u kunt een douaneoplossing uitvoeren om de sleutels van de inhoudsencryptie elders veilig op te slaan. Als u verkiest om de sleutels van de inhoudsencryptie in het gegevensbestand van LiveCycle ES verder op te slaan, volg de aanbevelingen die in &quot;het Beschermen van toegang tot gevoelige inhoud in het gegevensbestand&quot;in *Verharding en Veiligheid voor LiveCycle ES* worden geschetst.

Voor meer informatie over het verzekeren van verenigbaarheid met inhoud die gebruikend de Server 1.x van het Rights Management van Flash Media wordt verpakt, zie *de Verwijzing van API van de Toegang van de Adobe toegang*.
