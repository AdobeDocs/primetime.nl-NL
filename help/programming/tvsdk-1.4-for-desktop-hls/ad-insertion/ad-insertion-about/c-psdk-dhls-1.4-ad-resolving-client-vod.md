---
description: Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.
seo-description: Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.
seo-title: VOD en omzetten en invoegen
title: VOD en omzetten en invoegen
uuid: c1017483-5b4f-4d71-9589-fb2327b4572b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# VOD en invoegen{#vod-ad-resolving-and-insertion}

Voor video-on-demand (VOD)-inhoud voegt TVSDK de advertenties in de hoofdinhoud op en verbreekt deze door de tijdlijnduur te spreiden.

Voordat de inhoud wordt afgespeeld, lost TVSDK bekende advertenties op, voegt de hoofdinhoud in en voegt deze af zoals beschreven in een tijdlijn die door TVSDK wordt geretourneerd, en wordt de virtuele tijdlijn zo nodig opnieuw berekend.

TVSDK voegt advertenties op de volgende manieren in:

* **Pre-roll**, die vóór de inhoud is.
* **Halve rol**, die in de inhoud is.
* **Na de rol**, die na de inhoud is.

>[!IMPORTANT]
>
>Wanneer het uitvoeren van een douane `AdPolicySelector`, kan een verschillend beleid aan elk type van `AdBreakTimelineItem` (pre-rol, middenrol, of post-rol) in `AdPolicyInfo` worden gegeven, gebaseerd op het type van `AdBreakTimelineItem`. U kunt bijvoorbeeld inhoud halverwege de rol behouden nadat deze is afgespeeld, maar inhoud vóór de rol verwijderen nadat deze is afgespeeld.

Nadat het afspelen is gestart, kunnen er geen verdere wijzigingen in de inhoud plaatsvinden. Advertenties kunnen niet:

* Ingevoegd
* Verwijderd

   U kunt bijvoorbeeld geen ingebouwde advertenties uit de inhoud verwijderen voor een ad-vrije ervaring.
* Vervangen

   U kunt bijvoorbeeld geen ingebouwde advertenties vervangen door beoogde advertenties.

