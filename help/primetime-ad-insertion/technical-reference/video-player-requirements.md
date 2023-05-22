---
description: Alle videospelers moeten mogelijkheden bieden waarop de manifestserver vertrouwt om advertenties in te voegen en om het bijhouden van advertenties in te schakelen.
title: Vereisten voor videospeler
exl-id: 23134e4c-6902-4b97-bf15-4524f47850e7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Vereisten voor videospeler {#video-player-requirements}

Alle videospelers moeten mogelijkheden bieden waarop de manifestserver vertrouwt om advertenties in te voegen en om het bijhouden van advertenties in te schakelen.

Als u de API voor primetime en invoeging wilt gebruiken, moet een videospeler aan het volgende voldoen:

* Kan de positie van de afspeelkop bijhouden terwijl de inhoud wordt afgespeeld.
* Kan URL&#39;s bijhouden aanvragen op de opgegeven tijdstippen.
* Hiermee wordt uitgevoerd op een apparaatplatform dat HLS v3 of hoger ondersteunt, waaronder:

   * Afbrekingen van het PTS zoals aangegeven door `EXT-X-DISCONTINUITY` tags
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* Wordt uitgevoerd op een platform dat ondersteuning biedt voor HTTP-omleidingen en het parseren van JSON.
* Web-based spelers moeten op platforms lopen die CORS steunen.
