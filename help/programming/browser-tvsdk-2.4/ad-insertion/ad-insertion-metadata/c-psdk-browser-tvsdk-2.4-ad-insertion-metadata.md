---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-title: Metagegevens voor invoeging toevoegen
title: Metagegevens voor invoeging toevoegen
uuid: 8848c939-1f12-4145-8025-453b4fe79aae
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Overzicht {#ad-insertion-metadata-overview}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

Browser-TVSDK bevat de Adobe Primetime- en beslissingsbibliotheek. Uw toepassing moet de volgende vereiste AudidtudeSettings-informatie opgeven om uw inhoud ook reclame van de Adobe Primetime- en beslissingsserver op te nemen:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

   De uitgever wijst de media-id toe bij het verzenden van video-inhoud en advertentiegegevens naar de Adobe Primetime- en beslissingsserver. Deze id wordt gebruikt door Adobe Primetime en het besluit om gerelateerde advertentiegegevens voor de video op te halen van de server.

* (Optioneel), `defaultMediaId`waarmee wordt aangegeven welke advertenties worden aangeboden wanneer aan de volgende voorwaarden wordt voldaan:

   * Uw verzoek aan de advertentieserver is ongeldig, of de inhoud wordt verkeerd gevormd.
   * Adobe Primetime en besluitvorming hebben vertraging bij het verspreiden van de gegevens.
   * Een van de back-end processen voor Adobe Primetime en besluitvorming functioneert niet of is niet beschikbaar.
   >[!TIP]
   >
   >Adobe raadt u aan `defaultMediaId`.

* Uw `zoneID`bedrijf of website wordt geïdentificeerd door Adobe.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

   U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.