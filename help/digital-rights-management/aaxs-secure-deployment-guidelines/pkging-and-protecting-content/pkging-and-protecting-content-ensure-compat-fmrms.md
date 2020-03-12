---
seo-title: Compatibiliteit met Flash Media Rights Management Server 1.x garanderen
title: Compatibiliteit met Flash Media Rights Management Server 1.x garanderen
uuid: 0160ca02-ebe6-4090-bf32-1d1a46088844
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Compatibiliteit met Flash Media Rights Management Server 1.x garanderen{#ensure-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x en Adobe Access gebruiken verschillende metagegevens voor het verpakken van inhoud en het aanvragen van licenties. Adobe Access kan alleen FMRMS versie 1.x-inhoud gebruiken als de metagegevens zijn omgezet.

De SDK van Adobe Access ondersteunt twee opties voor het converteren van metagegevens:

* Off line (aanbevolen)

   Genereer de Adobe Access-metagegevens in een offlineproces en sla deze op voor gebruik wanneer een client hierom vraagt. Adobe raadt deze optie aan. Als de meta-gegevens off-line wordt geproduceerd, heeft de vergunningsserver geen toegang tot 1.x CEKs of de pakketreferentie nodig. Daarnaast biedt het omzetten van offline betere prestaties omdat de licentieserver de metagegevens niet in real-time hoeft te genereren.

* Op aanvraag

   Genereer de Adobe Access-metagegevens op aanvraag wanneer een client hierom vraagt. Wanneer een Adobe Access-client versie 1.x-inhoud downloadt, worden de DRM-metagegevens (ook wel de DRM-header genoemd) naar de Adobe Access SDK verzonden. De SDK converteert de DRM-metagegevens naar de huidige indeling. De SDK versleutelt en sluit de inhoudscoderingssleutel (CEK) in de metagegevens in en stuurt de inhoud terug naar de Adobe Access-client. (De Adobe Access 1.x-metagegevens bevatten niet de CEK.)

   Voor het converteren van de metagegevens hebt u toegang nodig tot de coderingssleutels voor Adobe Access 1.x-inhoud. Wanneer u migreert vanaf Flash Media Rights Management Server 1.x, kunt u de coderingssleutels voor inhoud blijven opslaan in de LiveCycle ES-database. U kunt ook een aangepaste oplossing implementeren om de coderingssleutels voor inhoud veilig elders op te slaan. Als u de coderingssleutels voor inhoud wilt blijven opslaan in de LiveCycle ES-database, volgt u de aanbevelingen in &quot;Toegang tot gevoelige inhoud in de database beveiligen&quot; in *Huring en beveiliging voor LiveCycle ES*.

Zie de *Adobe Access API-naslaggids voor* meer informatie over het garanderen van compatibiliteit met inhoud die is verpakt met Flash Media Rights Management Server 1.x.
