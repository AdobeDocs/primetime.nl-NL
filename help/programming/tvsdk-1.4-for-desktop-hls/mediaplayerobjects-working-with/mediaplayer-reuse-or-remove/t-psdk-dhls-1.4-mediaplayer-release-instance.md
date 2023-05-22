---
description: U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.
title: Een MediaPlayer-instantie en -bronnen opheffen
exl-id: 2a802754-5c51-4e5f-8c36-843074b487b5
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
