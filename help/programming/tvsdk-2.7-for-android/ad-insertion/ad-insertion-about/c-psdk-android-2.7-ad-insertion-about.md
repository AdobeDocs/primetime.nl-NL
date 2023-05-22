---
description: Toevoegen lost advertenties voor video-op-bestelling (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.
title: Advertenties invoegen
exl-id: e36cbbc5-330b-4840-bf6e-2efe58a67077
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Overzicht {#insert-ads-overview}

Toevoegen lost advertenties voor video-op-bestelling (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.

An *`ad break`* bevat een of meer advertenties die achtereenvolgens worden afgespeeld. TVSDK voegt advertenties in de hoofdinhoud in als leden van een of meer advertentieafbrekingen.

>[!NOTE]
>
>Als de advertentie fouten bevat, negeert TVSDK de advertentie.
