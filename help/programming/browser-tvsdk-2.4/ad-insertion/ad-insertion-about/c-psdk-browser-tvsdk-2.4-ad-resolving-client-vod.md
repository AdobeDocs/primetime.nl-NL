---
description: Voor video-on-demand-inhoud (VOD) voegt Browser TVSDK toe en verbreekt deze inhoud door de advertenties in de hoofdinhoud op te splitsen, zodat de tijdlijnduur langer wordt.
seo-description: Voor video-on-demand-inhoud (VOD) voegt Browser TVSDK toe en verbreekt deze inhoud door de advertenties in de hoofdinhoud op te splitsen, zodat de tijdlijnduur langer wordt.
seo-title: VOD en omzetten en invoegen
title: VOD en omzetten en invoegen
uuid: 34a30ae5-d553-4c5d-9829-8e5eaa41c104
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# VOD en omzetten en invoegen{#vod-ad-resolving-and-insertion}

Voor video-on-demand-inhoud (VOD) voegt Browser TVSDK toe en verbreekt deze inhoud door de advertenties in de hoofdinhoud op te splitsen, zodat de tijdlijnduur langer wordt.

Voordat de inhoud wordt afgespeeld, verhelpt Browser-TVSDK bekende advertenties, voegt de hoofdinhoud in en voegt deze af zoals wordt beschreven in een tijdlijn die wordt geretourneerd door Adobe Primetime en besluitvorming, en verwerkt indien nodig de virtuele tijdlijn opnieuw.

De browser TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die vóór de inhoud is.
* **Na de rol**, die na de inhoud is.

Nadat het afspelen is gestart, kunnen er geen verdere wijzigingen in de inhoud plaatsvinden. Advertenties kunnen niet:

* Ingevoegd
* Verwijderd

   U kunt bijvoorbeeld geen ingebouwde advertenties uit de inhoud verwijderen voor een ad-vrije ervaring.
* Vervangen

   U kunt bijvoorbeeld geen ingebouwde advertenties vervangen door beoogde advertenties.

