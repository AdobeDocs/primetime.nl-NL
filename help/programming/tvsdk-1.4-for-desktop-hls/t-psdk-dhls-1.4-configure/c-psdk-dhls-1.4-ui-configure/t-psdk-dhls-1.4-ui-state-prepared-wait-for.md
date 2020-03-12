---
description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
seo-description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
seo-title: Wacht op een geldige status
title: Wacht op een geldige status
uuid: 918ab021-3685-424a-b84e-683da0357724
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Wacht op een geldige status {#wait-for-a-valid-state}

Met TVSDK kunt u de standaardafspeelervaring voor live en video op verzoek (VOD) bepalen. TVSDK biedt methoden en eigenschappen voor de spelerinstantie die u kunt gebruiken om de gebruikersinterface van de speler te configureren. Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.

De speler doorloopt verschillende statussen. Wachten tot de speler de juiste status heeft, zorgt ervoor dat de mediabron correct is geladen. Als de speler niet minstens de vereiste status heeft, genereren veel spelermethoden `IllegalStateException`.

De vereiste status wordt gewoonlijk BEREID.

1. Om te bevestigen dat de status VOORBEREID is:

   Wanneer de speler initialiseert, wacht u tot TVSDK de callback voor de `MediaPlayerStatusChangeEvent.STATUS_CHANGED` gebeurtenis met de status PREPARED aanroept.

   Om te controleren of de huidige status van het `MediaPlayer` object ten minste PREPARED is.

   ```
   function getstatus():String;
   ```
