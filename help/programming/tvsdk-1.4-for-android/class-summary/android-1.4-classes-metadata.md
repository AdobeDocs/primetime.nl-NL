---
description: Deze klassen bieden metagegevens voor adverteren, naamruimten en tekstspatiëring.
title: Metagegevensklassen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Metagegevensklassen{#metadata-classes}

Deze klassen bieden metagegevens voor adverteren, naamruimten en tekstspatiëring.

Pakket: [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| Naam | Beschrijving |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | Klasse die eigenschappen verstrekt die voor het oplossen van advertenties voor een bepaald media punt zouden moeten worden gevormd. Alle vereiste eigenschappen moeten worden ingesteld om de speler te configureren voor het omzetten van advertenties. |
| AuditudeMetadata | Vervangen. Gebruik AuditudeSettings. |
| [AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Klasse die Java uitbreidt `AdvertisingMetadata` specifiek voor Phrase. Verstrekt eigenschappen die voor het oplossen van de advertenties van de Woorden voor een bepaald media punt moeten worden gevormd. U moet alle vereiste eigenschappen instellen, inclusief zone-id, media-id en de URL van de advertentieserver, om de speler zo te configureren dat advertenties met succes worden opgelost. |
| [Metagegevens](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | Definieert de algemene interface voor het configureren van alle beschikbare metagegevens voor de speler en aanvullende objecten. |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | Algemene gegevensstructuur-als klasse voor het opslaan van willekeurige sleutel-waarde paren. |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | Klasse voor de onbewerkte representatie van de metagegevens met tijdinstellingen die in een mediastream zijn ingevoegd. |
