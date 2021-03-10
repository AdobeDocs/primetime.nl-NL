---
description: Met TVSDK kunt u de standaardafspeelervaring voor live en video op verzoek (VOD) bepalen. TVSDK biedt methoden en eigenschappen voor de spelerinstantie die u kunt gebruiken om de gebruikersinterface van de speler te configureren.
title: Wacht op een geldige status
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Wacht op een geldige status {#wait-for-a-valid-state}

Met TVSDK kunt u de standaardafspeelervaring voor live en video op verzoek (VOD) bepalen. TVSDK biedt methoden en eigenschappen voor de spelerinstantie die u kunt gebruiken om de gebruikersinterface van de speler te configureren.

Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler zich in een geldige toestand bevinden.
De speler doorloopt verschillende statussen. Wanneer wordt gewacht totdat de speler in de juiste staat is, weet u zeker dat de mediabron is geladen. Als de speler zich niet in ten minste de vereiste status bevindt, genereren veel spelermethoden `IllegalStateException`.

De vereiste status wordt gewoonlijk BEREID.
