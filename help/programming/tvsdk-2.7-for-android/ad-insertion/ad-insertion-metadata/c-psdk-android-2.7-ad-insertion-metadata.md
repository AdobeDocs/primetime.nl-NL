---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
title: Metagegevens voor invoegen toevoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Overzicht {#ad-insertion-metadata-overview}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

TVSDK bevat de bibliotheek Primetime en Besluiten. Uw toepassing moet het volgende opgeven om uw inhoud ook reclame van de Primetime- en beslissingserver te laten opnemen `AuditudeSettings` informatie:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

  De uitgever wijst de media-id toe bij het verzenden van video-inhoud en advertentiegegevens naar de Adobe Primetime en de beslissingsserver. Deze id wordt gebruikt door Primetime en het besluit om gerelateerde advertentiegegevens voor de video op te halen van de server.

* (Optioneel) `defaultMediaId`, die aangeeft welke advertenties worden aangeboden wanneer aan de volgende voorwaarden wordt voldaan:

   * Uw verzoek aan de advertentieserver is ongeldig, of de inhoud wordt verkeerd gevormd.
   * Primetime en besluitvorming ondervinden vertragingen bij het verspreiden van de gegevens.
   * Een van de back-end processen voor primetime en beslissingen werkt niet of is niet beschikbaar.

  >[!TIP]
  >
  >Adobe raadt u aan `defaultMediaId`.

* Uw `zoneID`, die door Adobe wordt toegewezen, uw bedrijf of website identificeert.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

  U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.
