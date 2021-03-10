---
description: Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.
title: Controleren of StageVideo beschikbaar is
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 1%

---


# Controleren of StageVideo beschikbaar is{#check-whether-stagevideo-is-available}

Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.

Vanaf Flash 15 en hoger, als hardware `StageVideo` niet beschikbaar is, zal het terugvallen op software `StageVideo`. Voor Flash 14 en eerder kunt u bepalen of `StageVideo` beschikbaar is. Als `StageVideo` niet beschikbaar is, kunt u `StageVideoAvailabilityEvent` gebruiken om te begrijpen waarom het niet beschikbaar is.

1. Luister naar `StageVideoAvailabilityEvent` om te bepalen of `StageVideo` beschikbaar is.

   Bijvoorbeeld:

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Als `StageVideo` niet beschikbaar is, controleert `flash.media.StageVideoAvailabilityReason`.
