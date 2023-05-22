---
description: Gesloten bijschriften en ondertitels hebben enkele unieke verschillen en u kunt deze op verschillende manieren inschakelen.
title: Ondertitels en gesloten bijschriften
exl-id: 6602e9cf-d1e8-405b-83b7-bdd7d93b88f1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

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

      De `PTMediaPlayer` speelt de belangrijkste inhoud en advertenties, waar de belangrijkste inhoud live/lineair of VOD kon zijn, en de advertenties konden pre-rol, middenrol, of post-rol zijn.
   Hier volgen enkele aanvullende vereisten voor ondertitels in iOS:

   * Voor tijdstempels: `X-TIMESTAMP-MAP` waarde, die wordt opgegeven in het koptekstgedeelte van het dialoogvenster `WebVTT` bestand, moet overeenkomen met de tijdstempel van de video.

   * Voor het systeem moet u iOS 6.1 of hoger gebruiken.


>[!IMPORTANT]
>
>De vereisten voor ondertitels zijn niet van toepassing op gesloten bijschriften.
