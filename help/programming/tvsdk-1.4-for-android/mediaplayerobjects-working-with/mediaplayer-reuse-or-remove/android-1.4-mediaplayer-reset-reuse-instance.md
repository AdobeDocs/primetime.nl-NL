---
description: Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerState wordt bepaald.
title: Een MediaPlayer-instantie opnieuw instellen of gebruiken
exl-id: db8264f7-2f33-4441-86db-bb985edf7c3c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Een MediaPlayer-instantie opnieuw instellen, opnieuw gebruiken of verwijderen {#reset-or-reuse-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

Wanneer u een instantie MediaPlayer opnieuw instelt, wordt het teruggekeerd aan zijn niet geïnitialiseerde staat IDLE zoals die in MediaPlayerState wordt bepaald.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` -instantie maar moet een nieuwe instantie laden `MediaResource` (video-inhoud) en vervangt u de vorige instantie.

   Met opnieuw instellen kunt u de opdracht `MediaPlayer` instantie zonder de overhead van het vrijgeven van bronnen, opnieuw maken van de `MediaPlayer`en herallocatie van middelen.

* Wanneer de `MediaPlayer` bevindt zich in een FOUT-status en moet worden gewist.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de staat van de FOUT terug te krijgen.

1. Bellen `reset` om de `MediaPlayer` instantie in de niet-geïnitialiseerde status:

   ```java
   void reset() throws IllegalStateException; 
   ```

1. Gebruiken `MediaPlayer.replaceCurrentResource` om een andere te laden `MediaResource`.

   >[!TIP]
   >
   >Als u een fout wilt wissen, laadt u dezelfde `MediaResource`.

1. Wanneer u de `STATUS_CHANGED` callback van gebeurtenissen met de status PREPARED, start het afspelen.

## Een MediaPlayer-instantie en -bronnen opheffen{#release-a-mediaplayer-instance-and-resources}

U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.

Wanneer u een `MediaPlayer` object, de onderliggende hardwarebronnen die aan dit object zijn gekoppeld `MediaPlayer` -object wordt gedewijst.

Hier volgen enkele redenen om een MediaPlayer vrij te geven:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Een onnodige `MediaPlayer` -object kan leiden tot een continu batterijverbruik voor mobiele apparaten.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

1. Laat de `MediaPlayer`.

   ```java
   void release() throws IllegalStateException;
   ```

Na de `MediaPlayer` -instantie wordt vrijgegeven, kunt u deze niet meer gebruiken. Indien een methode van de `MediaPlayer` de interface wordt geroepen nadat het wordt vrijgegeven, en `IllegalStateException` wordt gegenereerd.
