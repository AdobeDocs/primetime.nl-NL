---
description: U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.
title: Een video afspelen en pauzeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
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

