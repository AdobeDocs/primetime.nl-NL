---
description: Wanneer het afspelen een advertentie-einde bereikt, een advertentie-einde doorgeeft of eindigt in een advertentie-einde, definieert TVSDK een standaardgedrag voor het plaatsen van de huidige afspeelkop.
seo-description: Wanneer het afspelen een advertentie-einde bereikt, een advertentie-einde doorgeeft of eindigt in een advertentie-einde, definieert TVSDK een standaardgedrag voor het plaatsen van de huidige afspeelkop.
seo-title: Afspelen met advertenties aanpassen
title: Afspelen met advertenties aanpassen
uuid: e7c9f4b1-15c9-43a2-be00-1ca4bfd17e43
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Overzicht {#customize-playback-with-ads-overview}

Wanneer het afspelen een advertentie-einde bereikt, een advertentie-einde doorgeeft of eindigt in een advertentie-einde, definieert TVSDK een standaardgedrag voor het plaatsen van de huidige afspeelkop.

>[!TIP]
>
>U kunt het standaardgedrag met de `AdPolicySelector` klasse overschrijven.

Het standaardgedrag varieert, afhankelijk van het feit of de gebruiker de advertentie doorgeeft tijdens het afspelen of door in een video te zoeken of deze snel terug te spoelen of terug te spoelen (truc).

U kunt het gedrag voor het afspelen en afspelen op de volgende manieren aanpassen:

* Sla de positie op waar de gebruiker het bekijken van de video heeft gestopt en hervat het afspelen op dezelfde positie in een toekomstige sessie.
* Als een advertentie-einde aan de gebruiker wordt voorgesteld, toon geen extra advertenties voor een aantal notulen, zelfs als de gebruiker aan een nieuwe positie zoekt.
* Als de inhoud na een paar minuten niet kan worden afgespeeld, start u de stream opnieuw of start u de stream over naar een andere bron voor dezelfde inhoud.

   Als u tijdens de afspeelsessie van de failover de gebruiker de mogelijkheid wilt bieden om advertenties over te slaan en de vorige mislukte positie te herstellen, kunt u pre-roll- en/of mid-roll-advertenties uitschakelen. TVSDK biedt methoden om pre- en mid-roll-advertenties over te slaan.