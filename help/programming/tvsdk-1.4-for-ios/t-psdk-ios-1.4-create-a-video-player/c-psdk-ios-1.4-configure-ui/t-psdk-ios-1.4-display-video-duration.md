---
description: U kunt de duur van de actieve inhoud weergeven.
seo-description: U kunt de duur van de actieve inhoud weergeven.
seo-title: De duur van de video weergeven
title: De duur van de video weergeven
uuid: 02042070-9c55-4cbb-9dc1-49987451eb8f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# De duur van de video weergeven {#display-the-duration-of-the-video}

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
