---
title: DRMStatusEvent-handlers maken
description: DRMStatusEvent-handlers maken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Een DRMStatusEvent-handler{#create-a-drmstatusevent-handler} maken

In het volgende voorbeeld wordt een gebeurtenishandler gemaakt die de statusinformatie van de DRM-inhoud uitvoert voor het Primetime-object dat de gebeurtenis heeft gestart.

Voeg een gebeurtenishandler toe aan een Primetime-object dat naar beveiligde inhoud wijst:

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

