---
description: Flash Media Rights Management Server 1.x en Adobe Primetime DRM gebruiken verschillende metagegevens voor het verpakken van inhoud en het aanvragen van licenties. Voor Primetime DRM om FMRMS versie 1.x-inhoud te gebruiken, moeten de metagegevens worden omgezet.
seo-description: Flash Media Rights Management Server 1.x en Adobe Primetime DRM gebruiken verschillende metagegevens voor het verpakken van inhoud en het aanvragen van licenties. Voor Primetime DRM om FMRMS versie 1.x-inhoud te gebruiken, moeten de metagegevens worden omgezet.
seo-title: Compatibiliteit met Flash Media Rights Management Server 1.x garanderen
title: Compatibiliteit met Flash Media Rights Management Server 1.x garanderen
uuid: dd70941e-9015-4fb0-b265-557b6252e051
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Compatibiliteit met Flash Media Rights Management Server 1.x garanderen {#ensuring-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x en Adobe Primetime DRM gebruiken verschillende metagegevens voor het verpakken van inhoud en het aanvragen van licenties. Voor Primetime DRM om FMRMS versie 1.x-inhoud te gebruiken, moeten de metagegevens worden omgezet.

De Primetime DRM SDK ondersteunt de volgende opties voor de conversie van metagegevens:

* Off line (aanbevolen)

   Genereer de DRM-metagegevens van Primetime in een offline proces en sla de metagegevens op totdat een client deze heeft aangevraagd. Als de meta-gegevens off-line wordt geproduceerd, heeft de vergunningsserver geen toegang tot 1.x CEKs of de pakketreferentie nodig. Het omzetten offline biedt betere prestaties omdat de licentieserver de metagegevens niet in real-time hoeft te genereren.
* Op aanvraag

   De DRM-metagegevens voor primetime worden gegenereerd wanneer de metagegevens worden aangevraagd door een client. Wanneer een Primetime DRM-client versie 1.x-inhoud downloadt, verzendt de client de DRM-metagegevens naar de Primetime DRM SDK. De SDK converteert de DRM-metagegevens naar de huidige indeling, versleutelt de CEK (Content Encryption Key) van de inhoud en sluit deze in de metagegevens in en stuurt de inhoud terug naar de Primetime DRM-client.

   >[!NOTE]
   >
   >De DRM 1.x-metagegevens van Primetime zijn niet inclusief de CEK.

   Voor het converteren van de metagegevens hebt u toegang nodig tot de Primetime DRM 1.x-coderingssleutels voor inhoud. Wanneer u migreert vanaf Flash Media Rights Management Server 1.x, kunt u de coderingssleutels voor inhoud blijven opslaan in de LiveCycle ES-database of een aangepaste oplossing implementeren om de coderingssleutels voor inhoud veilig op een andere locatie op te slaan. Als u besluit de coderingssleutels voor inhoud op te slaan in de LiveCycle ES-database, volgt u de aanbevelingen die worden beschreven in *Toegang tot gevoelige inhoud in de database* beschermen in **Verharden en Beveiliging voor LiveCycle® ES2**.

Zie de Adobe Primetime DRM API&#39;s in de Adobe Primetime API-referenties op de Adobe [Primetime API-referenties voor meer informatie over compatibiliteit met inhoud die is verpakt met Flash Media Rights Management Server 1.x](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).
