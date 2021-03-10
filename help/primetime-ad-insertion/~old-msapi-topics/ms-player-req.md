---
description: Alle videospelers moeten mogelijkheden bieden waarop de manifestserver vertrouwt om advertenties in te voegen en om het bijhouden van advertenties in te schakelen.
title: Vereisten voor videospeler
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Vereisten voor videospeler {#video-player-requirements}

Alle videospelers moeten mogelijkheden bieden waarop de manifestserver vertrouwt om advertenties in te voegen en om het bijhouden van advertenties in te schakelen.

Als u de API voor primetime en invoeging wilt gebruiken, moet een videospeler aan het volgende voldoen:

* Kan de positie van de afspeelkop bijhouden terwijl de inhoud wordt afgespeeld.
* Kan URL&#39;s bijhouden aanvragen op de opgegeven tijdstippen.
* Hiermee wordt uitgevoerd op een apparaatplatform dat HLS v3 of hoger ondersteunt, waaronder:

   * PTS-discontinuïteit zoals gemarkeerd door `EXT-X-DISCONTINUITY`-tags
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* Wordt uitgevoerd op een platform dat ondersteuning biedt voor HTTP-omleidingen en het parseren van JSON.
* Wordt uitgevoerd op een platform dat CORS ondersteunt.