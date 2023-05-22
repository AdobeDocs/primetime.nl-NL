---
description: U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.
title: Een video afspelen en pauzeren
exl-id: cb13ae62-f96b-4329-841f-aba885725d70
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Een video afspelen en pauzeren {#play-and-pause-a-video}

U kunt pauze- en afspeelknoppen toevoegen om de video te pauzeren of af te spelen.

1. Een pauze- of afspeelknop maken:
   1. Wacht tot de speler zich in minstens de voorbereide staat bevindt.
   1. Als u het afspelen wilt starten, roept u de `play` methode:

      ```java
      void play() throws MediaPlayerException;
      ```

   1. Als u het afspelen wilt pauzeren, roept u de `pause()` methode:

      ```java
      void pause() throws MediaPlayerException;
      ```

1. Gebruik de status veranderde gebeurteniscallback om op fouten te controleren of andere aangewezen acties te ondernemen.

   TVSDK roept deze callback aan `pause()` of `play()` en geeft informatie door over de statuswijziging, waaronder de nieuwe status, zoals gepauzeerd of afgespeeld.
