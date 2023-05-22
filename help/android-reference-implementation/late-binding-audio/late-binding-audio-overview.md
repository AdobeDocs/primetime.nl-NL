---
description: U kunt besturingselementen inschakelen en maken voor de laatste binding van audio.
title: Overzicht
exl-id: be3b41c5-1c30-430c-9baa-06b6496aceb4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Overzicht {#overview}

U kunt besturingselementen inschakelen en maken voor de laatste binding van audio.

De HLS-standaard staat streams met meerdere indelingen toe, wat betekent dat we de audio- en videotracks van een stream afzonderlijk van elkaar kunnen houden. De videotrack met meerdere uitvoeringen (bijvoorbeeld 240p, 480p, 720p en 1080p) en de audiotracks (bijvoorbeeld Engels, Spaans, Frans, Duits) kunnen afzonderlijk worden gecodeerd. De mediaspeler kiest vervolgens de gewenste video- en audiotracks en bindt deze op de client aan de kant van de client.

U kunt verschillende workflows implementeren, afhankelijk van de gebruikersinterface van de speler. De algemene workflow voor de Primetime-speler is als volgt:

1. Wanneer de eindgebruiker een video selecteert, wordt een lijst met beschikbare audiotracks voor dat media-item gevuld.
1. Wanneer de gebruiker op de knop Instellingen op de gebruikersinterface tikt, worden de audiotrackopties weergegeven.
1. Wanneer een audiotrack is geselecteerd, wordt de track de actieve audiotrack.
1. De eindgebruiker kan op de knop Instellingen tikken om terug te gaan naar de oorspronkelijke audiotrack.
