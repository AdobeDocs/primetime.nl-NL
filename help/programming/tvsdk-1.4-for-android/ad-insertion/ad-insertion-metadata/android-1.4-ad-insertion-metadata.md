---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
title: Metagegevens voor invoeging toevoegen
exl-id: 7245b42c-f3ba-43ec-b895-c1a2d66aa11f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Overzicht {#ad-insertion-metadata}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

TVSDK bevat de Primetime- en beslissingsbibliotheek. Uw toepassing moet het volgende opgeven om uw inhoud ook reclame van de Primetime- en beslissingsserver te laten opnemen `AuditudeSettings` informatie:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

   De uitgever wijst de `mediaID` wanneer u video-inhoud en advertentiegegevens naar de Adobe Primetime en de beslissingsserver verzendt. Deze id wordt gebruikt door Primetime en door beslissingen om gerelateerde advertentiegegevens voor de video op te halen van de server.

* (Optioneel) `defaultMediaId`, die aangeeft welke advertenties worden aangeboden wanneer aan de volgende voorwaarden wordt voldaan:

   * Uw verzoek aan de advertentieserver is ongeldig, of de inhoud wordt verkeerd gevormd.
   * Primetime en het besluit ervaren vertragingen bij het verspreiden van de gegevens.
   * Een van de back-end processen voor primetime en beslissingen werkt niet of is niet beschikbaar.

   >[!TIP]
   >
   >Adobe raadt u aan `defaultMediaId`.

* Uw `zoneID`, die wordt toegewezen door Adobe, uw bedrijf of website identificeert.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

   U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.
