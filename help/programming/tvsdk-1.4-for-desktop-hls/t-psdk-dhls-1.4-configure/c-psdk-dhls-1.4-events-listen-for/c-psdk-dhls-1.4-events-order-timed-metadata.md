---
description: TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.
title: Gebeurtenissen van getimede metagegevens
exl-id: 4c58b06e-5f70-452c-a743-55c4b6206711
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Gebeurtenissen van getimede metagegevens{#timed-metadata-events}

TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.

De speler implementeert handelingen op basis van de volgende gebeurtenissen:

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Wordt verzonden wanneer een metagegevens met tijdslimiet voor een ID3 is verwerkt.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Wordt verzonden wanneer metagegevens met tijdslimiet zijn verwerkt en er geen mogelijkheid is gevonden.
