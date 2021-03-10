---
description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
title: Wacht op een geldige status
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Wacht op een geldige status {#wait-for-a-valid-state}

Met TVSDK kunt u de standaardafspeelervaring voor live en video op verzoek (VOD) bepalen. TVSDK biedt methoden en eigenschappen voor de spelerinstantie die u kunt gebruiken om de gebruikersinterface van de speler te configureren.

Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.

Wachten tot de speler de juiste status heeft, zorgt ervoor dat de mediabron correct is geladen. Als de speler niet in minstens de vereiste status is, werpen vele spelermethodes `MediaPlayerException`.

De vereiste status wordt gewoonlijk BEREID. Wanneer dit voorkomt, voert de callback routine voor `StatusChangeEventListener.onStatusChanged()` uit.

1. Controleer `MediaPlayer.MediaPlayerStatus` om te bevestigen dat de status `PREPARED` is.
