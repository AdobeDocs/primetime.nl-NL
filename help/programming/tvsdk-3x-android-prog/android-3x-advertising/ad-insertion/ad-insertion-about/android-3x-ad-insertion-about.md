---
description: Toevoegen lost advertenties voor video-op-bestelling (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.
title: Advertenties invoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# Overzicht {#insert-ads-overview}

Toevoegen lost advertenties voor video-op-bestelling (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.

Een *`ad break`* bevat een of meer advertenties die achtereenvolgens worden afgespeeld. TVSDK voegt advertenties in de hoofdinhoud in als leden van een of meer advertentieafbrekingen.

>[!NOTE]
>
>Als de advertentie fouten bevat, negeert TVSDK de advertentie.