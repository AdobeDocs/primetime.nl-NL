---
description: Gesloten bijschriften en ondertitels hebben enkele unieke verschillen en u kunt deze op verschillende manieren inschakelen.
seo-description: Gesloten bijschriften en ondertitels hebben enkele unieke verschillen en u kunt deze op verschillende manieren inschakelen.
seo-title: Ondertitels en gesloten bijschriften
title: Ondertitels en gesloten bijschriften
uuid: 91daf0be-087a-4be5-86c2-f8b83da43a8f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Voorschriften voor ondertitels en gesloten bijschriften {#requirements-for-subtitles-and-closed-captions}

Gesloten bijschriften en ondertitels hebben enkele unieke verschillen en u kunt deze op verschillende manieren inschakelen.

Ondertitelingsstromen worden parallel met de hoofdinhoud uitgevoerd. Gesloten bijschriften maken deel uit van de gegevenspakketten van de MPEG-2-videostreams.

Houd rekening met de volgende vereisten voor gesloten bijschriften en ondertitels:

* **Ondertiteling**

   * Closed Captions hebben doorgaans dezelfde taal als de audio en vertegenwoordigen ook achtergrondgeluiden als tekst.
   * Gesloten bijschriften maken deel uit van de gegevenspakketten van de MPEG-2-videostreams in de videotransmissiestream.
   * Gesloten bijschriften worden ondersteund in de mate waarin dit wordt geboden door het AV Foundation-kader.

* **Ondertitels**

   * Ondertitels zijn doorgaans in een andere taal en bevatten geen achtergrondgeluiden.
   * Ondertitels bevinden zich in streams die parallel lopen met de hoofdinhoud.

      De `PTMediaPlayer` speler speelt de belangrijkste inhoud en advertenties af, waar de belangrijkste inhoud live/lineair of VOD kan zijn, en advertenties kunnen pre-rol, midden-rol, of post-rol zijn.
   Hier volgen enkele aanvullende vereisten voor ondertitels in iOS:

   * Voor tijdstempels moet de `X-TIMESTAMP-MAP` waarde, die is opgegeven in de koptekstsectie van het `WebVTT` bestand, overeenkomen met de tijdstempel van de video.

   * Voor het systeem moet u iOS 6.1 of hoger gebruiken.


>[!IMPORTANT]
>
>De vereisten voor ondertitels zijn niet van toepassing op gesloten bijschriften.

