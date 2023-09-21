---
description: Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.
title: VOD en omzetten en invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# VOD en omzetten en invoegen{#vod-ad-resolving-and-insertion}

Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.

Voordat de inhoud wordt afgespeeld, lost TVSDK bekende advertenties op, voegt de hoofdinhoud in en voegt deze af zoals wordt beschreven door een tijdlijn die door Adobe Primetime wordt geretourneerd en die de virtuele tijdlijn indien nodig opnieuw berekent.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die voor de inhoud ligt.
* **Midden rol**, die in de inhoud staat.
* **Na de rol**, die na de inhoud ligt.

Nadat het afspelen is gestart, kunnen er geen verdere wijzigingen in de inhoud plaatsvinden. Advertenties kunnen niet:

* Ingevoegd
* Verwijderd

  U kunt bijvoorbeeld geen ingebouwde advertenties uit de inhoud verwijderen voor een ad-vrije ervaring.
* Vervangen

  U kunt bijvoorbeeld geen ingebouwde advertenties vervangen door beoogde advertenties.
