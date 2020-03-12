---
seo-title: DRMErrorEvent-handlers maken
title: DRMErrorEvent-handlers maken
uuid: dde660fc-6899-47d4-97d4-46acda2db262
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# DRMErrorEvent-handlers maken{#create-a-drmerrorevent-handler}

Maak een gebeurtenishandler voor het verwerken van foutgebeurtenissen die vanaf Primetime worden verzonden wanneer een fout optreedt tijdens het afspelen van beveiligde inhoud.

Wanneer een toepassing een fout aantreft, wordt doorgaans een aantal opschoningstaken uitgevoerd. Vervolgens wordt de gebruiker op de hoogte gesteld van de fout en worden er opties geboden om het probleem op te lossen.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```

