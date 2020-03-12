---
description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-description: TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.
seo-title: Abonneren op aangepaste tags
title: Abonneren op aangepaste tags
uuid: fe8ba34d-66fc-43bb-b98e-659c1702d1e0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Abonneren op aangepaste tags{#subscribe-to-custom-tags}

TimedMetadata-objecten worden door TVSDK voorbereid voor geabonneerde tags telkens wanneer deze objecten in het inhoudsmanifest worden aangetroffen.

Voordat het afspelen begint, moet u zich op de tags abonneren.
Informatie over aangepaste tags in HLS-manifests:

Stel de aangepaste namen van tags globaal in door een array met aangepaste tags door te geven `setSubscribedTags` in `MediaPlayerItemConfig`.

>[!IMPORTANT]
>
>U moet het `#` voorvoegsel opnemen wanneer u werkt met HLS-streams.

Bijvoorbeeld:

```java
String[] array = new String[3]; 
array[0] = "#EXT-X-ASSET"; 
array[1] = "#EXT-X-BLACKOUT"; 
array[2] = "#EXT-OATCLS-SCTE35"; 
MediaPlayerItemConfig.setSubscribedTags(array);
```

