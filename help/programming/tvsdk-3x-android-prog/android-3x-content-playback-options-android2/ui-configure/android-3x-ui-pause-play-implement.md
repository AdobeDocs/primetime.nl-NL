---
description: U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.
seo-description: U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.
seo-title: Een video afspelen en pauzeren
title: Een video afspelen en pauzeren
uuid: 3778a1fb-929c-4579-a14c-561179473dea
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Een video afspelen en pauzeren {#play-and-pause-a-video}

U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.

1. Een pauze- of afspeelknop maken:
   1. Wacht tot de speler zich in minstens de voorbereide staat bevindt.
   1. Roep de `play` methode aan om het afspelen te starten:

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Roep de `pause()` methode op om het afspelen te pauzeren:

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Gebruik de status veranderde gebeurteniscallback om op fouten te controleren of andere aangewezen acties te ondernemen.

   TVSDK roept deze callback voor `pause()` of `play()` en gaat informatie over de statusverandering, met inbegrip van de nieuwe status, zoals gepauzeerd of het spelen over.