---
seo-title: DRMStatusEvent-handlers maken
title: DRMStatusEvent-handlers maken
uuid: 64f539d9-344c-4372-88b8-c8d098af9dd8
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# DRMStatusEvent-handlers maken{#create-a-drmstatusevent-handler}

In het volgende voorbeeld wordt een gebeurtenishandler gemaakt die de statusinformatie van de DRM-inhoud uitvoert voor het Primetime-object dat de gebeurtenis heeft gestart.

Voeg een gebeurtenishandler toe aan een Primetime-object dat naar beveiligde inhoud wijst:

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

