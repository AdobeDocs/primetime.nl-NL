---
description: TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.
title: Gebeurtenissen van getimede metagegevens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Gebeurtenissen van getimede metagegevens{#timed-metadata-events}

TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.

De speler implementeert handelingen op basis van de volgende gebeurtenissen:

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Wordt verzonden wanneer een metagegevens met een ID3-tijdinstelling is verwerkt.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Wordt verzonden wanneer metagegevens met tijdinstellingen zijn verwerkt en er geen mogelijkheid is gevonden.
