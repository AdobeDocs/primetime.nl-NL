---
description: TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.
seo-description: TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.
seo-title: Gebeurtenissen van getimede metagegevens
title: Gebeurtenissen van getimede metagegevens
uuid: 69c43701-6ffa-45fe-a104-fe81391222e7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# Timed metadata-gebeurtenissen{#timed-metadata-events}

TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.

De speler implementeert handelingen op basis van de volgende gebeurtenissen:

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Wordt verzonden wanneer een metagegevens met tijdslimiet voor een ID3 is verwerkt.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Wordt verzonden wanneer metagegevens met tijdslimiet zijn verwerkt en er geen mogelijkheid is gevonden.

