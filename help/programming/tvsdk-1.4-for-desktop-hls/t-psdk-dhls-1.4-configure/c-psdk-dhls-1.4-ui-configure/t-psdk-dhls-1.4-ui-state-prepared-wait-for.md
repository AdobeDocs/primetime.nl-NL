---
description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
title: Wacht op een geldige status
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Wacht op een geldige status {#wait-for-a-valid-state}

Met TVSDK kunt u de standaardafspeelervaring voor live en video op verzoek (VOD) bepalen. TVSDK biedt methoden en eigenschappen voor de spelerinstantie die u kunt gebruiken om de gebruikersinterface van de speler te configureren. Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.

De speler doorloopt verschillende statussen. Wachten tot de speler de juiste status heeft, zorgt ervoor dat de mediabron correct is geladen. Als de speler zich niet in ten minste de vereiste status bevindt, genereren veel spelermethoden `IllegalStateException`.

De vereiste status wordt gewoonlijk BEREID.

1. Om te bevestigen dat de status VOORBEREID is:

   Wanneer de speler initialiseert, wacht u tot TVSDK de callback voor de `MediaPlayerStatusChangeEvent.STATUS_CHANGED` gebeurtenis met de status PREPARED.

   Om te controleren of de huidige status van `MediaPlayer` object ten minste PREPARED is.

   ```
   function getstatus():String;
   ```
