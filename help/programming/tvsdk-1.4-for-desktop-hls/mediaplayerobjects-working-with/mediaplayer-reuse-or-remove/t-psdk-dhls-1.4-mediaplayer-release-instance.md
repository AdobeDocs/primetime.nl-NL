---
description: U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.
title: Een MediaPlayer-instantie en -bronnen opheffen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Een MediaPlayer-instantie en -bronnen opheffen{#release-a-mediaplayer-instance-and-resources}

U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.

Wanneer u een `MediaPlayer` object, de onderliggende hardwarebronnen die aan dit object zijn gekoppeld `MediaPlayer` -object wordt gedewijst.

Hier volgen enkele redenen om een `MediaPlayer`:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

1. Laat de `MediaPlayer`.

   ```
   function release():void;
   ```

Na de `MediaPlayer` -instantie wordt vrijgegeven, kunt u deze niet meer gebruiken. Indien een methode van de `MediaPlayer` de interface wordt geroepen nadat het wordt vrijgegeven, en `IllegalStateException` wordt gegenereerd.
