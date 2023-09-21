---
title: Voorroladvertenties uitschakelen
description: Voorroladvertenties uitschakelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 0%

---

# Voorroladvertenties uitschakelen{#disable-pre-roll-ads}

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
