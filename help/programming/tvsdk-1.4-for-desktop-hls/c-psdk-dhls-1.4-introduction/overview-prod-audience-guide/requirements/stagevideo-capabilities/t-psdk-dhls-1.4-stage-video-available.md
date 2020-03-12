---
description: Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.
seo-description: Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.
seo-title: Controleren of StageVideo beschikbaar is
title: Controleren of StageVideo beschikbaar is
uuid: 09c39442-cb9a-4892-af99-3d3d9bf1d4a7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Controleren of StageVideo beschikbaar is{#check-whether-stagevideo-is-available}

Als StageVideo niet beschikbaar is en uw toepassing probeert StageVideo te gebruiken, geeft de TVSDK geen fout weer. Uw toepassing kan bepalen of StageVideo beschikbaar is door te luisteren naar de StageVideoAvailabilityEvent.

Vanaf Flash 15 en hoger geldt dat wanneer hardware niet beschikbaar `StageVideo` is, deze terugvalt op software `StageVideo`. Voor Flash 14 en lager kunt u bepalen of deze beschikbaar `StageVideo` zijn. Als `StageVideo` het niet beschikbaar is, kunt u gebruiken `StageVideoAvailabilityEvent` om te begrijpen waarom het niet beschikbaar is.

1. Luister naar `StageVideoAvailabilityEvent` om te bepalen of `StageVideo` beschikbaar is.

   Bijvoorbeeld:

   ```
   private function onStageAvailable(event:StageVideoAvailabilityEvent):void {
       if (event.availability != StageVideoAvailability.AVAILABLE) {
           // process the error scenario here
       }
   }
   ```

1. Als `StageVideo` niet beschikbaar is, controleer `flash.media.StageVideoAvailabilityReason`.
