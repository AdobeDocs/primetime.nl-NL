---
description: U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.
seo-description: U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.
seo-title: Een video afspelen en pauzeren
title: Een video afspelen en pauzeren
uuid: 66fefead-7f1d-46ed-a23e-381f25697978
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Een video afspelen en pauzeren {#play-and-pause-a-video}

U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.

1. Een pauze- of afspeelknop maken:
   1. Wacht tot de speler zich in minstens de voorbereide staat bevindt.
   1. Roep de methode `play` aan om het afspelen te starten:

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Roep de methode `pause()` aan om het afspelen te pauzeren:

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Gebruik de status veranderde gebeurteniscallback om op fouten te controleren of andere aangewezen acties te ondernemen.

   TVSDK roept deze callback voor `pause()` of `play()` en gaat informatie over de statusverandering, met inbegrip van de nieuwe status, zoals gepauzeerd of het spelen over.

