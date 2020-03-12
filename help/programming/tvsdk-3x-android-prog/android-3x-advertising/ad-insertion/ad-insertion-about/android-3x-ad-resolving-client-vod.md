---
description: Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.
seo-description: Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.
seo-title: VOD-advertentie omzetten en invoegen
title: VOD-advertentie omzetten en invoegen
uuid: b7124cab-441b-4b38-ac83-300ab9e5f9ec
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# VOD-advertenties omzetten en invoegen {#resolve-and-insert-vod-ad}

Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.

Voordat de inhoud wordt afgespeeld, lost TVSDK bekende advertenties op, voegt de hoofdinhoud in en verbreekt deze volgens een tijdlijn die door Adobe Primetime en besluitvorming wordt geretourneerd, en wordt de virtuele tijdlijn indien nodig opnieuw berekend.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die vóór de inhoud wordt geplaatst.
* **Halftoonraster**, midden in de inhoud.
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