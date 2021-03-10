---
description: U kunt de duur van de actieve inhoud weergeven.
title: De duur van de video weergeven
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# De duur van de video {#display-the-duration-of-the-video} weergeven

U kunt de duur van de actieve inhoud weergeven.

Een weergave tijdens de videoduur implementeren met de volgende voorbeeldcode:

    De eigenschap &#39;PTMediaPlayer`, [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange), bevat het huidige bereik van doorzoekbare vensters:
    
    * Voor VOD is dit bereik het gehele VOD-inhoudsbereik, inclusief advertenties.
    * Voor live/lineair vertegenwoordigt dit bereik het doorzoekbare venster.
    
    Zie [TVSDK 1.4 for iOS API Reference] (https://help.adobe.com/en_US/primetime/api/psdk/appledoc/index.html) voor meer informatie over de API.

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
