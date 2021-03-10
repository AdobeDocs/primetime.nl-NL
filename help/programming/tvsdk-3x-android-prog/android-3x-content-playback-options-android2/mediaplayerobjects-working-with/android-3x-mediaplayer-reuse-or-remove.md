---
description: U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.
title: Een MediaPlayer-instantie opnieuw gebruiken of verwijderen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# Een MediaPlayer-instantie {#reuse-or-remove-a-mediaplayer-instance} opnieuw gebruiken of verwijderen

U kunt een MediaPlayer-instantie die u niet meer nodig hebt opnieuw instellen, opnieuw gebruiken of vrijgeven.

## Een MediaPlayer-instantie {#section_E6A2446A2D0B4ACD9EA980685B2E57D9} opnieuw instellen of gebruiken

Wanneer u een `MediaPlayer` instantie terugstelt, is het teruggekeerd aan zijn niet geïnitialiseerde status IDLE zoals bepaald in `MediaPlayerStatus`.

Deze bewerking is handig in de volgende gevallen:

* U wilt een `MediaPlayer` instantie opnieuw gebruiken maar moet een nieuwe `MediaResource` (video-inhoud) laden en de vorige instantie vervangen.

   Met resetting kunt u de `MediaPlayer`-instantie opnieuw gebruiken zonder de overhead van het vrijgeven van bronnen, het opnieuw maken van de `MediaPlayer` en het opnieuw toewijzen van bronnen.

* Wanneer `MediaPlayer` in FOUTstatus is en moet worden ontruimd.

   >[!IMPORTANT]
   >
   >Dit is de enige manier om van de status van de FOUT terug te krijgen.

   1. Roep `reset` aan om de `MediaPlayer` instantie aan zijn niet-geïnitialiseerde status terug te keren:

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. Gebruik `MediaPlayer.replaceCurrentResource()` om een andere `MediaResource` te laden.

      >[!NOTE]
      >
      >Als u een fout wilt wissen, laadt u dezelfde `MediaResource`.

   1. Wanneer u de `STATUS_CHANGED` gebeurteniscallback met `PREPARED` status ontvangt, begin de playback.

## Een MediaPlayer-instantie en -bronnen opheffen {#section_13A0914AFF784943ABC343F7EB249C4E}

U zou een `MediaPlayer` instantie en middelen moeten vrijgeven wanneer u `MediaResource` niet meer nodig hebt.

Wanneer u een `MediaPlayer` voorwerp vrijgeeft, worden de onderliggende hardwaremiddelen die met dit `MediaPlayer` voorwerp worden geassocieerd deassigned.

Hier zijn enkele redenen om een `MediaPlayer` vrij te geven:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Als u een onnodig `MediaPlayer`-object instantieert, kan dit leiden tot een continu batterijverbruik voor mobiele apparaten.
* Indien meerdere instanties
Als dezelfde video-codec niet wordt ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

* Geef `MediaPlayer` vrij.

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >Nadat de `MediaPlayer` instantie wordt vrijgegeven, kunt u het niet meer gebruiken. Als om het even welke methode van de `MediaPlayer` interface wordt geroepen nadat het wordt vrijgegeven, wordt `MediaPlayerException` geworpen.