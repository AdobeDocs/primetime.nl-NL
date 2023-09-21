---
description: Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.
title: Controleren of StageVideo beschikbaar is
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Controleren of StageVideo beschikbaar is{#check-whether-stagevideo-is-available}

Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.

Vanaf Flash 15 en hoger, wanneer hardware `StageVideo` is niet beschikbaar, wordt de software opnieuw geïnstalleerd `StageVideo`. Voor Flash 14 en eerder kunt u bepalen of `StageVideo` is beschikbaar. Indien `StageVideo` is niet beschikbaar, kunt u `StageVideoAvailabilityEvent` om te begrijpen waarom het niet beschikbaar is.

1. Luisteren naar `StageVideoAvailabilityEvent` bepalen of `StageVideo` is beschikbaar.

   Bijvoorbeeld:

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Indien `StageVideo` is niet beschikbaar, controle `flash.media.StageVideoAvailabilityReason`.
