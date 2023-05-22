---
description: Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.
title: Wacht op een geldige status
exl-id: bfd77163-7ca8-41e1-8b97-2d6a765f5ccd
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Wacht op een geldige status {#wait-for-a-valid-status}

Met TVSDK kunt u de standaardafspeelervaring voor live en video op verzoek (VOD) bepalen. TVSDK biedt methoden en eigenschappen voor de spelerinstantie die u kunt gebruiken om de gebruikersinterface van de speler te configureren.

Voordat u de meeste methoden van de TVSDK-speler kunt gebruiken, moet de speler een geldige status hebben.

Wachten tot de speler de juiste status heeft, zorgt ervoor dat de mediabron correct is geladen. Als de speler niet in minstens de vereiste status is, genereren veel spelermethoden `MediaPlayerException`.

De vereiste status wordt gewoonlijk BEREID. Wanneer dit voorkomt, de callback routine voor `StatusChangeEventListener.onStatusChanged()` wordt uitgevoerd.

Bevestig dat de status `PREPARED`, controle `MediaPlayer.MediaPlayerStatus`.
