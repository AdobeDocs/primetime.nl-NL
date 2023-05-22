---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
title: Metagegevens voor invoeging toevoegen
exl-id: 8d6cb371-8666-4b55-b828-0f1d495e7fb7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Overzicht {#ad-insertion-metadata-overview}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

Browser-TVSDK bevat de Adobe Primetime en de beslissingsbibliotheek. Uw toepassing moet de volgende vereiste AudidtudeSettings-informatie opgeven om uw inhoud ook reclame van de Adobe Primetime- en beslissingsserver te kunnen opnemen:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

   De uitgever wijst de media-id toe bij het verzenden van video-inhoud en advertentiegegevens naar de Adobe Primetime en de beslissingsserver. Deze id wordt gebruikt door Adobe Primetime en besluit gerelateerde advertentiegegevens voor de video op te halen van de server.

* (Optioneel) `defaultMediaId`, die aangeeft welke advertenties worden aangeboden wanneer aan de volgende voorwaarden wordt voldaan:

   * Uw verzoek aan de advertentieserver is ongeldig, of de inhoud wordt verkeerd gevormd.
   * Adobe Primetime en de besluitvorming hebben vertraging bij de verspreiding van de gegevens.
   * Een van de Adobe Primetime en back-endprocessen voor beslissingen werkt niet of is niet beschikbaar.

   >[!TIP]
   >
   >Adobe raadt u aan `defaultMediaId`.

* Uw `zoneID`, die wordt toegewezen door Adobe, uw bedrijf of website identificeert.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

   U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.
