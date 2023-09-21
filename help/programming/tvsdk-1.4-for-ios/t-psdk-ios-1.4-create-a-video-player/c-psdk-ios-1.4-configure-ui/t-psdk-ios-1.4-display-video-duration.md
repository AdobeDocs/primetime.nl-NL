---
description: U kunt de duur van de actieve inhoud weergeven.
title: De duur van de video weergeven
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# De duur van de video weergeven {#display-the-duration-of-the-video}

U kunt de duur van de actieve inhoud weergeven.

Een weergave tijdens de videoduur implementeren met de volgende voorbeeldcode:

De `PTMediaPlayer` eigenschap, [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange), bevat het huidige bereik van doorzoekbare vensters:

* Voor VOD is dit bereik het gehele VOD-inhoudsbereik, inclusief advertenties.
* Voor live/lineair vertegenwoordigt dit bereik het doorzoekbare venster.

Zie voor meer informatie over de API [TVSDK 1.4 voor iOS API-naslag](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
