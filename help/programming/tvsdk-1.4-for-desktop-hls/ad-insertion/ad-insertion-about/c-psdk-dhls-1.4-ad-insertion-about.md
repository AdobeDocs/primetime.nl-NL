---
description: Toevoegen lost advertenties voor video-op-verzoek (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.
title: Advertenties invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---

# Overzicht {#inserting-ads-overview}

Toevoegen lost advertenties voor video-op-verzoek (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.

An *`ad break`* bevat een of meer advertenties die achtereenvolgens worden afgespeeld. TVSDK voegt advertenties in de hoofdinhoud in als leden van een of meer advertentieafbrekingen.

## Voorroladvertenties uitschakelen {#disable-preroll-ads}

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
