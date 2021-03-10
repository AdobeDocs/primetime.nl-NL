---
description: Deze klassen bieden informatie over advertenties die binnen een tijdlijn voorkomen.
title: Tijdlijnadvertentieklassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---


# Tijdlijnadvertentieklassen{#timeline-advertising-classes}

Deze klassen bieden informatie over advertenties die binnen een tijdlijn voorkomen.

Pakket: [com.adobe.mediacore.timeline.advertence](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/package-summary.html)

Pakket: [com.adobe.mediacore.timeline.advertence.auditude](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/package-summary.html)

| Naam | Beschrijving |
|--- |--- |
| [Advertentie](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/Ad.html) | Klasse die de abstractie van de Advertentie bepaalt en alle advertentiemateriaal houdt. Deze wordt gedefinieerd door een unieke id, een duur en een `MediaResource`. De `MediaResource` bevat de URL waar de daadwerkelijke inhoud van de advertentie zich bevindt. |
| [AdAsset](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdAsset.html) | Klasse die een element vertegenwoordigt dat moet worden weergegeven. Klasse die een advertentie-element vertegenwoordigt. |
| [AdBreak](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreak.html) | Klasse die een verenigde weergave biedt op meerdere advertenties die op een bepaald punt tijdens het afspelen worden afgespeeld. |
| [AdBreakPlacement](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPlacement.html) | bewerkingsklasse voor plaatsing van regeleinde toevoegen. |
| [AdBreakPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdBreakPolicy.html) | Opsomming waarmee het beleid voor het afspelen van advertenties wordt gedefinieerd voor het omzeilen van advertenties door de gebruiker tijdens het zoeken. |
| [AdClick](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdClick.html) | Klasse die een klikinstantie vertegenwoordigt die aan activa wordt geassocieerd. Deze instantie bevat informatie over de doorklikken-URL en de titel die kunnen worden gebruikt om extra informatie aan de gebruiker te verstrekken. |
| [AdPolicyInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicyInfo.html) | Interface die eigenschappen voor API-aanroepen AdPolicySelector definieert. Deze eigenschappen bieden de context voor het afdwingen van elk advertentiegedrag. |
| [AdPolicySelector](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/AdPolicySelector.html) | An ad policy selector interface for enforcing and behavior. Toepassingen kunnen met deze interface in overeenstemming zijn door alle vereiste methoden te implementeren of door de bestaande standaardbeleidsselectorklasse uit te breiden om specifiek gedrag aan te passen. |
| `auditude.AuditudeAdProvider` | Vervangen. Gebruik AuditudeResolver. |
| [AuditudeResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeResolver.html) | Klasse die de primetime afhandelt en het oplossen in het proces van de Woorden. |
| [AuditudeTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/auditude/AuditudeTracker.html) | Klasse die de interface ContentTracker implementeert en gebeurtenissen Primetime ad-tracking definieert. |
| [ContentResolver](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentResolver.html) | Klasse die het ad-resolving deel in het proces van de Woorden behandelt. |
| [ContentTracker](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/ContentTracker.html) | Interface die het protocol bepaalt dat u moet uitvoeren als u een ad-volgende module wilt tot stand brengen die wordt ontworpen om met de bibliotheek of een douane en spoortrekker te integreren. Deze interface vereist dat u definieert hoe ad-progress-gebeurtenissen worden gerapporteerd aan het externe ad-tracking-systeem. |
| [PlacementInformation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/advertising/PlacementInformation.html) | Klasse die een verzoek om plaatsingsinformatie onttrekt. Aan elke opgeloste advertentie moet één plaatsingsinformatie zijn gekoppeld. De plaatsingsinformatie beschrijft waar de advertentie op de tijdlijn moet worden geplaatst. Het bevat informatie zoals: <ul><li>Plaatsing (in ms) </li><li>Type plaatsing (vóór, halverwege of na de rollover) </li><li>Duur van het hoofdinhoudsegment dat op het punt staat te worden vervangen</li></ul> |
