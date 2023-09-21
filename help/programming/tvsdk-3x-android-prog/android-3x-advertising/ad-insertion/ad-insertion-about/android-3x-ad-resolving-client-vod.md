---
description: Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.
title: VOD-advertentie omzetten en invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# VOD-advertenties omzetten en invoegen {#resolve-and-insert-vod-ad}

Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.

Voordat de inhoud wordt afgespeeld, lost TVSDK bekende advertenties op, voegt de hoofdinhoud in en voegt deze af zoals wordt beschreven door een tijdlijn die door Adobe Primetime wordt geretourneerd en die de virtuele tijdlijn indien nodig opnieuw berekent.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die voor de inhoud wordt geplaatst.
* **Midden rol**, die midden in de inhoud ligt.
* **Na de rol**, die na de inhoud wordt geplaatst.

>[!TIP]
>
>Nadat het afspelen is gestart, kunnen er geen verdere wijzigingen in de inhoud plaatsvinden.

Advertenties kunnen niet:

* Ingevoegd
* Verwijderd

  U kunt bijvoorbeeld geen ingebouwde advertenties uit de inhoud verwijderen voor een ad-vrije ervaring.
* Vervangen

  U kunt bijvoorbeeld geen ingebouwde advertenties vervangen door beoogde advertenties.
