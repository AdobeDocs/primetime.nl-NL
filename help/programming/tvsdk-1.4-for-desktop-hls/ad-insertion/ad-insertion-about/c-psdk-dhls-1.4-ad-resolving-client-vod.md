---
description: Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.
title: VOD en omzetten en invoegen
exl-id: 6f02c7fc-028d-442f-92d4-9efa671b7f02
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# VOD en omzetten en invoegen{#vod-ad-resolving-and-insertion}

Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.

Voordat de inhoud wordt afgespeeld, lost TVSDK bekende advertenties op, voegt de hoofdinhoud in en voegt deze af zoals beschreven in een tijdlijn die door TVSDK wordt geretourneerd, en wordt de virtuele tijdlijn zo nodig opnieuw berekend.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die voor de inhoud ligt.
* **Midden rol**, die in de inhoud staat.
* **Na de rol**, die na de inhoud ligt.

>[!IMPORTANT]
>
>Bij het implementeren van een aangepaste `AdPolicySelector`kan aan elk type `AdBreakTimelineItem` (vóór de rol, halverwege de rol of na de rol) in `AdPolicyInfo`op basis van het type `AdBreakTimelineItem`. U kunt bijvoorbeeld inhoud halverwege de rol behouden nadat deze is afgespeeld, maar inhoud vóór de rol verwijderen nadat deze is afgespeeld.

Nadat het afspelen is gestart, kunnen er geen verdere wijzigingen in de inhoud plaatsvinden. Advertenties kunnen niet:

* Ingevoegd
* Verwijderd

   U kunt bijvoorbeeld geen ingebouwde advertenties uit de inhoud verwijderen voor een ad-vrije ervaring.
* Vervangen

   U kunt bijvoorbeeld geen ingebouwde advertenties vervangen door beoogde advertenties.
