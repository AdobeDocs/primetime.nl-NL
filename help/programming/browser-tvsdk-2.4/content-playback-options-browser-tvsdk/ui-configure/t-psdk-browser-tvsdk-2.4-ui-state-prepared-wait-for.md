---
description: Voordat u de meeste methoden van de Browser-TVSDK-speler kunt gebruiken, moet de speler zich in een geldige toestand bevinden.
seo-description: Voordat u de meeste methoden van de Browser-TVSDK-speler kunt gebruiken, moet de speler zich in een geldige toestand bevinden.
seo-title: Wacht op een geldige status
title: Wacht op een geldige status
uuid: 0add29a8-fbd8-483a-8c99-e4bc6de9e3d3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Wacht op een geldige status {#wait-for-a-valid-state}

Voordat u de meeste methoden van de Browser-TVSDK-speler kunt gebruiken, moet de speler zich in een geldige toestand bevinden.

De speler doorloopt verschillende statussen. Wanneer wordt gewacht totdat de speler in de juiste staat is, weet u zeker dat de mediabron is geladen. Als de speler zich niet in ten minste de vereiste status bevindt, genereren veel spelermethoden `IllegalStateException`.

De vereiste status wordt gewoonlijk BEREID.

1. Om te bevestigen dat de status BEREID is:

   Wanneer de speler initialiseert, wacht u tot Browser TVSDK de `AdobePSDK.MediaPlayerStatusChangeEvent` gebeurtenis verzendt met een `event.status` van `MediaPlayerStatus.PREPARED`.

   Om te controleren of de huidige status van het MediaPlayer-object ten minste PREPARED is.

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```

