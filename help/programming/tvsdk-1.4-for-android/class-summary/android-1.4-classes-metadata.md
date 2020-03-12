---
description: Deze klassen bieden metagegevens voor adverteren, naamruimten en tekstspatiëring.
seo-description: Deze klassen bieden metagegevens voor adverteren, naamruimten en tekstspatiëring.
seo-title: Metagegevensklassen
title: Metagegevensklassen
uuid: 6d5099c8-d562-4635-9ef0-068cc6fb9f82
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Metagegevensklassen{#metadata-classes}

Deze klassen bieden metagegevens voor adverteren, naamruimten en tekstspatiëring.

Pakket: [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| Naam | Beschrijving |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | Klasse die eigenschappen verstrekt die voor het oplossen van advertenties voor een bepaald media punt zouden moeten worden gevormd. Alle vereiste eigenschappen moeten worden ingesteld om de speler te configureren voor het omzetten van advertenties. |
| AuditudeMetadata | Vervangen. Gebruik AuditudeSettings. |
| [AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Klasse die Java `AdvertisingMetadata` specifiek voor Woorden uitbreidt. Verstrekt eigenschappen die voor het oplossen van de advertenties van de Woorden voor een bepaald media punt moeten worden gevormd. U moet alle vereiste eigenschappen instellen, inclusief zone-id, media-id en de URL van de advertentieserver, om de speler zo te configureren dat advertenties met succes worden opgelost. |
| [Metagegevens](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | Definieert de algemene interface voor het configureren van alle beschikbare metagegevens voor de speler en aanvullende objecten. |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | Algemene gegevensstructuur-als klasse voor het opslaan van willekeurige sleutel-waarde paren. |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | Klasse voor de onbewerkte representatie van de metagegevens met tijdinstellingen die in een mediastream zijn ingevoegd. |