---
description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
title: Wacht op een geldige status
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Wacht op een geldige status {#wait-for-a-valid-state}

Met TVSDK kunt u de standaardafspeelervaring voor live en video op verzoek (VOD) bepalen. TVSDK biedt methoden en eigenschappen voor de spelerinstantie die u kunt gebruiken om de gebruikersinterface van de speler te configureren. Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.

De speler doorloopt verschillende statussen. Wachten tot de speler de juiste status heeft, zorgt ervoor dat de mediabron correct is geladen. Als de speler niet in minstens de vereiste status is, werpen vele spelermethodes `IllegalStateException`.

De vereiste status wordt gewoonlijk BEREID.

1. Om te bevestigen dat de status VOORBEREID is:

   Wanneer de speler initialiseert, wacht op TVSDK om callback voor de `MediaPlayerStatusChangeEvent.STATUS_CHANGED` gebeurtenis met PREPARED status te roepen.

   Om te controleren of de huidige status van het object `MediaPlayer` ten minste PREPARED is.

   ```
   function getstatus():String;
   ```
