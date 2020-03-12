---
description: 'null'
seo-description: 'null'
seo-title: Voorroladvertenties uitschakelen
title: Voorroladvertenties uitschakelen
uuid: 2e307a58-49f2-43d6-908b-97684ad6e3d3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

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

