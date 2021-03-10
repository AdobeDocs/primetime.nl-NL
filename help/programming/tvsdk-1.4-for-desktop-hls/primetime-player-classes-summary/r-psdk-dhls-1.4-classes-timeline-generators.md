---
description: Deze klassen helpen u bij het detecteren van kansen in een tijdlijn voor de plaatsing van inhoud, zoals advertenties.
title: Klassen van tijdlijngeneratoren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Klassen voor tijdlijngeneratoren{#timeline-generators-classes}

Deze klassen helpen u bij het detecteren van kansen in een tijdlijn voor de plaatsing van inhoud, zoals advertenties.

Pakket: [com.adobe.mediacore.timeline.generators](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/package-detail.html)

| Naam | Beschrijving |
|---|---|
| [AdSignalingModeOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/AdSignalingModeOpportunityGenerator.html) | Klasse die een eerste kans voor de gespecificeerde reclame signalerende wijze creeert. |
| [OpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGenerator.html) | Basisklasse voor alle opportuniteitsgeneratoren. |
| [OpportunityGeneratorClient](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/OpportunityGeneratorClient.html) | Interface die door opportuniteitsgenerators wordt gebruikt om met TVSDK-componenten te communiceren. |
| [SpliceOutOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/SpliceOutOpportunityGenerator.html) | Klasse die de afspeeltijdlijn bewaakt en plaatsingsmogelijkheden detecteert die als SpliceOut-opmerkingen in het manifest zijn ingevoegd. |
| [TimedMetadataOpportunityGenerator](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/generators/TimedMetadataOpportunityGenerator.html) | Standaardimplementatie van een opportuniteitsgenerator die getimede metagegevens gebruikt om advertentiemogelijkheden te detecteren en te genereren. |