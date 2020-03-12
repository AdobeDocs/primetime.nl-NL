---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-title: Metagegevens voor invoeging toevoegen
title: Metagegevens voor invoeging toevoegen
uuid: f40ed53b-eba1-4f70-a29c-90cac51e8a9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Overzicht {#ad-insertion-metadata}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

TVSDK bevat de Primetime- en beslissingsbibliotheek. Uw toepassing moet de volgende vereiste `AuditudeSettings` informatie opgeven om uw inhoud ook reclame van de Primetime- en beslissingsserver te kunnen opnemen:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

   De uitgever wijst de inhoud toe `mediaID` wanneer video-inhoud en advertentiegegevens naar de Adobe Primetime- en beslissingsserver worden verzonden. Deze id wordt gebruikt door Primetime en door beslissingen om gerelateerde advertentiegegevens voor de video op te halen van de server.

* (Optioneel), `defaultMediaId`waarmee wordt aangegeven welke advertenties worden aangeboden wanneer aan de volgende voorwaarden wordt voldaan:

   * Uw verzoek aan de advertentieserver is ongeldig, of de inhoud wordt verkeerd gevormd.
   * Primetime en het besluit ervaren vertragingen bij het verspreiden van de gegevens.
   * Een van de back-end processen voor primetime en beslissingen werkt niet of is niet beschikbaar.
   >[!TIP]
   >
   >Adobe raadt u aan `defaultMediaId`.

* Uw `zoneID`bedrijf of website wordt geïdentificeerd door Adobe.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

   U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.