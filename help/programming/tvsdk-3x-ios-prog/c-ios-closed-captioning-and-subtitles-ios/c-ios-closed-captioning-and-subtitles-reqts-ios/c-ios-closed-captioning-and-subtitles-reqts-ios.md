---
description: Gesloten bijschriften en ondertitels hebben enkele unieke verschillen en u kunt deze op verschillende manieren inschakelen.
title: Voorschriften voor ondertitels en gesloten bijschriften
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Vereisten voor ondertitels en gesloten bijschriften {#requirements-for-subtitles-and-closed-captions}

Gesloten bijschriften en ondertitels hebben enkele unieke verschillen en u kunt deze op verschillende manieren inschakelen.

Ondertitelingsstromen worden parallel met de hoofdinhoud uitgevoerd. Gesloten bijschriften maken deel uit van de gegevenspakketten van de MPEG-2-videostreams.

Houd rekening met de volgende vereisten voor gesloten bijschriften en ondertitels:

* **Ondertiteling**

   * Gesloten bijschriften hebben doorgaans dezelfde taal als de audio en vertegenwoordigen ook achtergrondgeluiden als tekst.
   * Gesloten bijschriften maken deel uit van de gegevenspakketten van de MPEG-2-videostreams in de videotransmissiestream.
   * Gesloten bijschriften worden ondersteund in de mate waarin dit wordt geboden door het AV Foundation-kader.

* **Ondertitels**

   * Ondertitels zijn doorgaans in een andere taal en bevatten geen achtergrondgeluiden.
   * Ondertitels bevinden zich in streams die parallel lopen met de hoofdinhoud.

      Met `PTMediaPlayer` worden de belangrijkste inhoud en advertenties afgespeeld, waarbij de hoofdinhoud live/lineair of VOD kan zijn en de advertenties pre-roll, mid-roll of post-roll kunnen zijn.
   Hier volgen enkele aanvullende vereisten voor ondertitels in iOS:

   * Voor tijdstempels moet de waarde `X-TIMESTAMP-MAP`, die is opgegeven in de koptekstsectie van het `WebVTT`-bestand, overeenkomen met de tijdstempel van de video.

   * Voor het systeem moet u iOS 6.1 of hoger gebruiken.


>[!IMPORTANT]
>
>De vereisten voor ondertitels zijn niet van toepassing op gesloten bijschriften.