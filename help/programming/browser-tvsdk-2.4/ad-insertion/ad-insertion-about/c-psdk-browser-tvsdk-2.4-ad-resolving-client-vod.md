---
description: Voor video-on-demand-inhoud (VOD) voegt Browser TVSDK toe en verbreekt deze inhoud door de advertenties in de hoofdinhoud op te splitsen, zodat de tijdlijnduur langer wordt.
title: VOD en omzetten en invoegen
exl-id: c2a2f14b-c90d-47fc-9dcc-eff8b1491dde
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# VOD en omzetten en invoegen{#vod-ad-resolving-and-insertion}

Voor video-on-demand-inhoud (VOD) voegt Browser TVSDK toe en verbreekt deze inhoud door de advertenties in de hoofdinhoud op te splitsen, zodat de tijdlijnduur langer wordt.

Voordat de inhoud wordt afgespeeld, lost Browser-TVSDK bekende advertenties op, voegt de hoofdinhoud in en voegt deze af zoals wordt beschreven door een tijdlijn die door Adobe Primetime wordt geretourneerd en die de virtuele tijdlijn indien nodig opnieuw berekent.

De browser TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die voor de inhoud ligt.
* **Na de rol**, die na de inhoud ligt.

Nadat het afspelen is gestart, kunnen er geen verdere wijzigingen in de inhoud plaatsvinden. Advertenties kunnen niet:

* Ingevoegd
* Verwijderd

   U kunt bijvoorbeeld geen ingebouwde advertenties uit de inhoud verwijderen voor een ad-vrije ervaring.
* Vervangen

   U kunt bijvoorbeeld geen ingebouwde advertenties vervangen door beoogde advertenties.
