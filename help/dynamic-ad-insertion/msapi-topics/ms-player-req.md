---
description: Alle videospelers moeten mogelijkheden bieden waarop de manifestserver vertrouwt om advertenties in te voegen en om het bijhouden van advertenties in te schakelen.
seo-description: Alle videospelers moeten mogelijkheden bieden waarop de manifestserver vertrouwt om advertenties in te voegen en om het bijhouden van advertenties in te schakelen.
seo-title: Vereisten voor videospeler
title: Vereisten voor videospeler
uuid: 29593d67-2901-4d9e-a08f-23c8a7667283
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Vereisten voor videospeler {#video-player-requirements}

Alle videospelers moeten mogelijkheden bieden waarop de manifestserver vertrouwt om advertenties in te voegen en om het bijhouden van advertenties in te schakelen.

Als u de API voor primetime en invoeging wilt gebruiken, moet een videospeler aan het volgende voldoen:

* Kan de positie van de afspeelkop bijhouden terwijl de inhoud wordt afgespeeld.
* Kan URL&#39;s bijhouden aanvragen op de opgegeven tijdstippen.
* Hiermee wordt uitgevoerd op een apparaatplatform dat HLS v3 of hoger ondersteunt, waaronder:

   * Afbrekingen van het PTS zoals gemarkeerd door `EXT-X-DISCONTINUITY` tags
   * `EXT-X-DISCONTINUITY-SEQUENCE`
   * `EXT-X-PROGRAM-DATE-TIME`
   * `EXT-X-START`

* Wordt uitgevoerd op een platform dat ondersteuning biedt voor HTTP-omleidingen en het parseren van JSON.
* Wordt uitgevoerd op een platform dat CORS ondersteunt.