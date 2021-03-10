---
title: DRMErrorEvent-handlers maken
description: DRMErrorEvent-handlers maken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# Een DRMErrorEvent-handler{#create-a-drmerrorevent-handler} maken

Maak een gebeurtenishandler voor het verwerken van foutgebeurtenissen die vanaf Primetime worden verzonden wanneer een fout optreedt tijdens het afspelen van beveiligde inhoud.

Wanneer een toepassing een fout aantreft, wordt doorgaans een aantal opschoningstaken uitgevoerd. Vervolgens wordt de gebruiker op de hoogte gesteld van de fout en worden er opties geboden om het probleem op te lossen.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```

