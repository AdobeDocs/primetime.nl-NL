---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
seo-title: Een vroege en eindresultaat implementeren
title: Een vroege en eindresultaat implementeren
uuid: 984b6ed0-c929-49a3-9553-e30d1a7758ed
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# Een vroege en eindresultaat implementeren{#implementing-an-early-ad-break-return}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

>[!NOTE]
>
>U moet zich abonneren op de splice out/in-advertentiemarkeringen ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`en `#EXT-X-CUE`).

Hieronder volgen enkele vereisten die u in overweging wilt nemen:

* Parseermarkeringen zoals `EXT-X-CUE-IN` (of een equivalent markeerteken) die in de lineaire of FER streams worden weergegeven.

   Registreer de markeringen als de teller voor een vroege terugkeerpunt. Alleen afspelen `adBreaks` tot deze markeeringspositie tijdens afspelen, die de duur van de `adBreak` markering door de `EXE-X-CUE-OUT` regelafstandmarkering overschrijft.

* Als er twee `EXT-X-CUE-IN` markeringen voor dezelfde `EXT-X-CUE-OUT` markering bestaan, telt de eerste `EXT-X-CUE-IN` markering die wordt weergegeven.

* Als het `EXE-X-CUE-IN` markeerteken in de tijdlijn verschijnt zonder een `EXT-X-CUE-OUT` markeerteken, wordt het `EXE-X-CUE-IN` markeerteken genegeerd.

   Als in een live stream de `EXT-X-CUE-OUT` markering voor regelafstand net uit het venster is verplaatst, reageert de TVSDK niet op het venster.

* Wanneer er een vroege terugkeer van een advertentie-onderbreking is, `adBreak` speelt het spel tot playhead op de originele positie terugkeert toen het advertentierak zou moeten beëindigen en hervat het spelen van de belangrijkste inhoud van die positie.

## SpliceOut en SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` en `SpliceIn` markeertekens geven het begin en het einde van het advertentieeinde aan. De duur van het `SpliceOut` type `EXE-X-CUE` markering kan nul zijn en het `SpliceIn` type `EXE-X-CUE` markering markeert het einde van het ad-einde. Ze worden in één label weergegeven en verschillen per type.

**Eén markering met verschillende typen**

Hier ziet u bijvoorbeeld één markering met verschillende typen:

```
#EXTM3U#EXT-X-TARGETDURATION:10
#EXT-X-VERSION:3
#EXT-X-MEDIA-SEQUENCE:44
  
#EXTINF:9.9,
https://server-host/path/file44.ts
#EXTINF:4.2,
https://server-host/path/file45.ts
  
#EXT-X-CUE:TYPE="SpliceOut",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138",AVAIL-NUM="1",AVAILS-EXPECTED="10"
#EXTINF:5.8,
https://server-host/path/file46.ts
#EXTINF:9.9,
https://server-host/path/file47.ts
...
#EXTINF:9.9,
https://server-host/path/file56.ts
#EXTINF:4.2,
https://server-host/path/file57.ts
#EXT-X-CUE:TYPE="SpliceIn",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138"
#EXTINF:9.9,
https://server-host/path/file58.ts
```

Als de duur van het `SpliceOut` type nul is in het ene markeerteken met verschillende typen, `SpliceOut` moeten de tekens `SpliceIn` en de tekens voor elk advertentiepad samenwerken. Momenteel is een `SpliceOut` markeerteken met een tijdsduur groter dan nul en heeft het geen `SpliceIn` markeertekens voor het naast elkaar plaatsen nodig.

**Twee afzonderlijke markeringen**

Het meer typische scenario is een `SpliceOut` teller met een duur niet-nul en die niet de het telegraferen `SpliceIn` tellers nodig heeft. Hier wordt een `SpliceIn` markeerteken voor de koppeling het einde van de advertentie aangegeven tijdens het afspelen van een advertentie, maar het ad-einde wordt kort bij de `SpliceIn` markeerpositie geknipt en de hoofdinhoud wordt op deze positie afgespeeld.

Hier ziet u bijvoorbeeld twee afzonderlijke markeringen:

```
#EXT-X-CUE-OUT:ID=105,DURATION=30.0,TIME=1081.08
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589090425811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589150485811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589210545811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589270605811,format=m3u8-aapl-v4)
#EXT-X-CUE-IN:ID=105,TIME=1105.104
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589330665811,format=m3u8-aapl-v4)
```

