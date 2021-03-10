---
description: Flash Media Rights Management Server 1.x en Adobe Primetime DRM gebruiken verschillende metagegevens voor het verpakken van inhoud en het aanvragen van licenties. Voor Primetime DRM om FMRMS versie 1.x-inhoud te gebruiken, moeten de metagegevens worden omgezet.
title: Compatibiliteit met Flash Media Rights Management Server 1.x waarborgen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Compatibiliteit met Flash Media Rights Management Server 1.x {#ensuring-compatibility-with-flash-media-rights-management-server-x} waarborgen

Flash Media Rights Management Server 1.x en Adobe Primetime DRM gebruiken verschillende metagegevens voor het verpakken van inhoud en het aanvragen van licenties. Voor Primetime DRM om FMRMS versie 1.x-inhoud te gebruiken, moeten de metagegevens worden omgezet.

De Primetime DRM SDK ondersteunt de volgende opties voor de conversie van metagegevens:

* Off line (aanbevolen)

   Genereer de DRM-metagegevens van Primetime in een offline proces en sla de metagegevens op totdat een client deze heeft aangevraagd. Als de meta-gegevens off-line wordt geproduceerd, heeft de vergunningsserver geen toegang tot 1.x CEKs of de pakketreferentie nodig. Het omzetten offline biedt betere prestaties omdat de licentieserver de metagegevens niet in real-time hoeft te genereren.
* Op aanvraag

   De DRM-metagegevens voor primetime worden gegenereerd wanneer de metagegevens worden aangevraagd door een client. Wanneer een Primetime DRM-client versie 1.x-inhoud downloadt, verzendt de client de DRM-metagegevens naar de Primetime DRM SDK. De SDK converteert de DRM-metagegevens naar de huidige indeling, versleutelt de CEK (Content Encryption Key) van de inhoud en sluit deze in de metagegevens in en stuurt de inhoud terug naar de Primetime DRM-client.

   >[!NOTE]
   >
   >De DRM 1.x-metagegevens van Primetime zijn niet inclusief de CEK.

   Voor het converteren van de metagegevens hebt u toegang nodig tot de Primetime DRM 1.x-coderingssleutels voor inhoud. Wanneer u van de Server 1.x van het Rights Management van de Media van de Flash Media migreert, kunt u de sleutels van de inhoudsencryptie in het gegevensbestand blijven opslaan van LiveCycle ES of een douaneoplossing uitvoeren om de sleutels van de inhoudsencryptie veilig op een andere plaats op te slaan. Als u besluit om de sleutels van de inhoudsencryptie in het gegevensbestand van LiveCycle ES op te slaan, volg de aanbevelingen die in *het Beschermen van toegang tot gevoelige inhoud in het gegevensbestand* in **het Verharden en Veiligheid voor LiveCycle® ES2** worden geschetst.

Zie de Adobe Primetime DRM API&#39;s op [Adobe Primetime API References](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References) voor meer informatie over het garanderen van compatibiliteit met inhoud die is verpakt met Flash Media Rights Management Server 1.x.
