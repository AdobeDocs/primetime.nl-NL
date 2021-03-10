---
description: U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.
title: Een MediaPlayer-instantie en -bronnen opheffen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---


# Een MediaPlayer-instantie en -bronnen opheffen{#release-a-mediaplayer-instance-and-resources}

U zou een instantie MediaPlayer en middelen moeten vrijgeven wanneer u niet meer MediaResource nodig hebt.

Wanneer u een `MediaPlayer` voorwerp vrijgeeft, worden de onderliggende hardwaremiddelen die met dit `MediaPlayer` voorwerp worden geassocieerd deassigned.

Hier zijn enkele redenen om een `MediaPlayer` vrij te geven:

* Het vasthouden van onnodige bronnen kan de prestaties beïnvloeden.
* Als meerdere instanties van dezelfde video-codec niet worden ondersteund op een apparaat, kan het afspelen mislukken bij andere toepassingen.

1. Geef `MediaPlayer` vrij.

   ```
   function release():void;
   ```

Nadat de `MediaPlayer` instantie wordt vrijgegeven, kunt u het niet meer gebruiken. Als om het even welke methode van de `MediaPlayer` interface wordt geroepen nadat het wordt vrijgegeven, wordt `IllegalStateException` geworpen.