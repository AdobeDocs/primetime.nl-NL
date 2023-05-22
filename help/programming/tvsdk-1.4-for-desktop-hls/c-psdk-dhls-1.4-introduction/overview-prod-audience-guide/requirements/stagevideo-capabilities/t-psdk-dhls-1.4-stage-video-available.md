---
description: Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.
title: Controleren of StageVideo beschikbaar is
exl-id: 24136a14-8d7d-4569-9911-fac4e2de3227
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Controleren of StageVideo beschikbaar is{#check-whether-stagevideo-is-available}

Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.

Vanaf Flash 15 en hoger, wanneer hardware `StageVideo` is niet beschikbaar, wordt de software opnieuw geïnstalleerd `StageVideo`. Voor Flash 14 en eerder kunt u bepalen of `StageVideo` is beschikbaar. Indien `StageVideo` is niet beschikbaar, kunt u `StageVideoAvailabilityEvent` om te begrijpen waarom het niet beschikbaar is.

1. Luisteren naar `StageVideoAvailabilityEvent` om te bepalen of `StageVideo` is beschikbaar.

   Bijvoorbeeld:

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Indien `StageVideo` is niet beschikbaar, controle `flash.media.StageVideoAvailabilityReason`.
