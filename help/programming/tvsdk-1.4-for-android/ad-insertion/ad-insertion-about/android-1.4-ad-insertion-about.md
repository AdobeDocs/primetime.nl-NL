---
description: Toevoegen lost advertenties voor video-op-bestelling (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.
title: Advertenties invoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Overzicht {#insert-ads-overview}

Toevoegen lost advertenties voor video-op-bestelling (VOD), voor live streaming en voor lineair streamen met het bijhouden van advertenties en het afspelen van advertenties op. TVSDK doet de vereiste verzoeken aan de advertentieserver, ontvangt informatie over advertenties voor de opgegeven inhoud en plaatst de advertenties in fasen.

Een advertentie-einde bevat een of meer advertenties die achtereenvolgens worden afgespeeld. TVSDK voegt advertenties in de hoofdinhoud in als leden van een of meer advertentieafbrekingen.

>[!TIP]
>
>Als de advertentie fouten bevat, negeert TVSDK de advertentie.
