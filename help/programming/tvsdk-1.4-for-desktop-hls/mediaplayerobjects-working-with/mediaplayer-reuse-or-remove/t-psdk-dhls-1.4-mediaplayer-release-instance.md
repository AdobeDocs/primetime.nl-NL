---
description: U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.
seo-description: U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.
seo-title: Een MediaPlayer-instantie en -bronnen opheffen
title: Een MediaPlayer-instantie en -bronnen opheffen
uuid: e7b2112e-8add-4789-9345-5f829d39d639
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Een MediaPlayer-instantie en -bronnen opheffen{#release-a-mediaplayer-instance-and-resources}

U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.

Wanneer u een `MediaPlayer` object loslaat, worden de onderliggende hardwarebronnen die aan dit `MediaPlayer` object zijn gekoppeld, gedeallocatie.

Hier volgen enkele redenen om een `MediaPlayer`:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

1. Laat de muisknop los `MediaPlayer`.

   ```
   function release():void;
   ```

Nadat de `MediaPlayer` instantie is losgelaten, kunt u deze niet meer gebruiken. Als om het even welke methode van de `MediaPlayer` interface wordt geroepen nadat het wordt vrijgegeven, `IllegalStateException` wordt geworpen.