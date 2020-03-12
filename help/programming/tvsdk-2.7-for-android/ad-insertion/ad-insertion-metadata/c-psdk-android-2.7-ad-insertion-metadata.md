---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-title: Metagegevens voor invoeging toevoegen
title: Metagegevens voor invoeging toevoegen
uuid: ee4dd8b8-4c41-4f01-be50-60f4c7dc962d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Overzicht {#ad-insertion-metadata-overview}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

TVSDK bevat de bibliotheek Primetime en Besluiten. Uw toepassing moet de volgende vereiste `AuditudeSettings` informatie verschaffen om uw inhoud ook reclame van de Primetime- en beslissingserver te kunnen opnemen:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

   De uitgever wijst de media-id toe bij het verzenden van video-inhoud en advertentiegegevens naar de Adobe Primetime- en beslissingsserver. Deze id wordt gebruikt door Primetime en het besluit om gerelateerde advertentiegegevens voor de video op te halen van de server.

* (Optioneel), `defaultMediaId`waarmee wordt aangegeven welke advertenties worden aangeboden wanneer aan de volgende voorwaarden wordt voldaan:

   * Uw verzoek aan de advertentieserver is ongeldig, of de inhoud wordt verkeerd gevormd.
   * Primetime en besluitvorming ondervinden vertragingen bij het verspreiden van de gegevens.
   * Een van de back-end processen voor primetime en beslissingen werkt niet of is niet beschikbaar.
   >[!TIP]
   >
   >Adobe raadt u aan `defaultMediaId`.

* Uw `zoneID`bedrijf of website wordt geïdentificeerd door Adobe.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

   U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.