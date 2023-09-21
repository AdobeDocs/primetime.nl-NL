---
description: Voordat u de meeste methoden van de Browser-TVSDK-speler kunt gebruiken, moet de speler zich in een geldige toestand bevinden.
title: Wacht op een geldige status
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Wacht op een geldige status {#wait-for-a-valid-state}

Voordat u de meeste methoden van de Browser-TVSDK-speler kunt gebruiken, moet de speler zich in een geldige toestand bevinden.

De speler doorloopt verschillende statussen. Wanneer wordt gewacht totdat de speler in de juiste staat is, weet u zeker dat de mediabron is geladen. Als de speler zich niet in ten minste de vereiste status bevindt, genereren veel spelermethoden `IllegalStateException`.

De vereiste status wordt gewoonlijk BEREID.

1. Om te bevestigen dat de status BEREID is:

   Wanneer de speler wordt geïnitialiseerd, wacht u tot Browser TVSDK de `AdobePSDK.MediaPlayerStatusChangeEvent` gebeurtenis met een `event.status` van `MediaPlayerStatus.PREPARED`.

   Om te controleren of de huidige status van het MediaPlayer-object ten minste PREPARED is.

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```
