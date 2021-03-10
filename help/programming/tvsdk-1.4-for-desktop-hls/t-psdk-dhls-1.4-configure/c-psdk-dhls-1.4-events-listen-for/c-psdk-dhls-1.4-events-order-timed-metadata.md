---
description: TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.
title: Gebeurtenissen van getimede metagegevens
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Timed metadata-gebeurtenissen{#timed-metadata-events}

TVSDK verzendt gebeurtenissen met getimede metagegevens en genereert getimede metagegevens wanneer standaard- of aangepaste tags worden aangetroffen of wanneer een afspeellijst in een manifest verandert. Gebeurtenissen worden verzonden in de volgorde waarin ze in het manifest voorkomen.

De speler implementeert handelingen op basis van de volgende gebeurtenissen:

* `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`: Wordt verzonden wanneer een metagegevens met tijdslimiet voor een ID3 is verwerkt.
* `TimedMetadataEvent.TIMED_METADATA_SKIPPED`: Wordt verzonden wanneer metagegevens met tijdslimiet zijn verwerkt en er geen mogelijkheid is gevonden.

