---
description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
exl-id: 8b84c7f1-713a-46b4-8eb7-d699a79e74b7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Een MediaPlayer-instantie opnieuw gebruiken of verwijderen {#reuse-or-remove-a-mediaplayer-instance}

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

## Een MediaPlayer-instantie opnieuw instellen of gebruiken {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

Wanneer u een `MediaPlayer` -instantie, wordt de niet-geïnitialiseerde IDLE-status van de instantie hersteld, zoals gedefinieerd in `MediaPlayerStatus`.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` -instantie maar moet een nieuwe instantie laden `MediaResource` (video-inhoud) en vervangt u de vorige instantie.

   Met opnieuw instellen kunt u de opdracht `MediaPlayer` instantie zonder de overhead van het vrijgeven van bronnen, opnieuw maken van de `MediaPlayer`en herallocatie van middelen.

* Wanneer de `MediaPlayer` bevindt zich in de status ERROR en moet worden gewist.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de status van de FOUT terug te krijgen.

   1. Bellen `reset` om de `MediaPlayer` -instantie naar de niet-geïnitialiseerde status:

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Gebruiken `MediaPlayer.replaceCurrentResource()` om een andere te laden `MediaResource`.

      >[!NOTE]
      >
      >Als u een fout wilt wissen, laadt u dezelfde `MediaResource`.

   1. Wanneer u de `STATUS_CHANGED` gebeurteniscallback met `PREPARED` status, start het afspelen.

## Een MediaPlayer-instantie en -bronnen opheffen {#section_13A0914AFF784943ABC343F7EB249C4E}

U moet een `MediaPlayer` instantie en bronnen wanneer u de `MediaResource`.

Wanneer u een `MediaPlayer` object, de onderliggende hardwarebronnen die aan dit object zijn gekoppeld `MediaPlayer` -object wordt gedewijst.

Hier volgen enkele redenen om een `MediaPlayer`:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Een onnodige `MediaPlayer` geïnstantieerde objecten kunnen leiden tot een continu batterijverbruik voor mobiele apparaten.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

* Laat de `MediaPlayer`.

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >Na de `MediaPlayer` -instantie wordt vrijgegeven, kunt u deze niet meer gebruiken. Indien een methode van de `MediaPlayer` de interface wordt geroepen nadat het wordt vrijgegeven, a `MediaPlayerException` wordt gegenereerd.
