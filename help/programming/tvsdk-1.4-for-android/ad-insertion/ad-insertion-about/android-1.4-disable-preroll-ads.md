---
title: Voorroladvertenties uitschakelen
description: Voorroladvertenties uitschakelen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 0%

---


# Voorroladvertenties{#disable-pre-roll-ads} uitschakelen

Om pre-rol onbruikbaar te maken, verander de standaardopportuniteitsgenerators om niet de pre-rolvraag te maken. De standaard opportuniteitsgeneratoren zijn:

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
result.push(new AdSignalingModeOpportunityGenerator()); 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```

Om pre-rol op levende stromen onbruikbaar te maken, verander hierboven om slechts SpliceOutOpportunityGenerator te omvatten:

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
if (preroll_enabled == true) { result.push(new AdSignalingModeOpportunityGenerator()); } 
 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```

