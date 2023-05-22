---
description: Wanneer het afspelen een advertentie-einde bereikt, een advertentie-einde doorgeeft of eindigt in een advertentie-einde, definieert TVSDK een standaardgedrag voor het plaatsen van de huidige afspeelkop.
title: Afspelen met advertenties aanpassen
exl-id: f67c6914-ff65-4afe-95e2-16160df3921f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Overzicht {#customize-playback-with-ads}

Wanneer het afspelen een advertentie-einde bereikt, een advertentie-einde doorgeeft of eindigt in een advertentie-einde, definieert TVSDK een standaardgedrag voor het plaatsen van de huidige afspeelkop.

>[!TIP]
>
>U kunt het standaardgedrag overschrijven door de opdracht `AdBreakPolicySelector` klasse.

Het standaardgedrag varieert, afhankelijk van het feit of de gebruiker de advertentie doorgeeft tijdens het afspelen of door in een video te zoeken of deze snel terug te spoelen of terug te spoelen (truc).

U kunt het gedrag voor het afspelen en afspelen op de volgende manieren aanpassen:

* Sla de positie op waar de gebruiker het bekijken van de video heeft gestopt en hervat het afspelen op dezelfde positie in een toekomstige sessie.
* Als een advertentie-einde aan de gebruiker wordt voorgesteld, toon geen extra advertenties voor een paar minuten, zelfs als de gebruiker aan een nieuwe positie zoekt.
* Als de inhoud na een paar minuten niet kan worden afgespeeld, start u de stream opnieuw of start u de stream over naar een andere bron voor dezelfde inhoud.

   Als u tijdens de afspeelsessie van de failover de gebruiker de mogelijkheid wilt bieden om advertenties over te slaan en de vorige mislukte positie te herstellen, kunt u pre-roll- en/of mid-roll-advertenties uitschakelen. TVSDK biedt methoden om pre- en mid-roll-advertenties over te slaan.
