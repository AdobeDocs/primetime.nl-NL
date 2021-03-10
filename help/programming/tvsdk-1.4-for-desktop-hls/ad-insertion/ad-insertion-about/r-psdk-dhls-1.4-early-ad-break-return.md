---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
title: Een vroege en eindresultaat implementeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# Een vroege terugkeer voor een onderbreking implementeren{#implementing-an-early-ad-break-return}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

>[!NOTE]
>
>U moet zich abonneren op de splice out/in-advertentiemarkeringen ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN` en `#EXT-X-CUE`).

Hieronder volgen enkele vereisten die u in overweging wilt nemen:

* Parseermarkeringen zoals `EXT-X-CUE-IN` (of een equivalent markeringslabel) die in de lineaire of FER streams worden weergegeven.

   Registreer de markeringen als de teller voor een vroege terugkeerpunt. Alleen `adBreaks` afspelen tot deze markeerpositie tijdens het afspelen, die de duur van de `adBreak` gemarkeerd door de regelafstandmarkering `EXE-X-CUE-OUT` overschrijft.

* Als twee `EXT-X-CUE-IN` tellers voor de zelfde `EXT-X-CUE-OUT` teller bestaan, is de eerste `EXT-X-CUE-IN` teller die verschijnt die tellen.

* Als het `EXE-X-CUE-IN` markeerteken in de tijdlijn verschijnt zonder een regelafstandmarkering `EXT-X-CUE-OUT`, wordt het `EXE-X-CUE-IN` markeerteken verwijderd.

   Als de regelafstandmarkering `EXT-X-CUE-OUT` in een live stream net uit het venster is verplaatst, reageert de TVSDK niet op het venster.

* Wanneer er een vroege terugkeer van een advertentieonderbreking is, speelt `adBreak` tot playhead op de originele positie terugkeert toen het advertentierak om zou moeten beëindigen en hervat het spelen van de belangrijkste inhoud van die positie.

## SpliceOut en SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` en  `SpliceIn` markeertekens geven het begin en het einde van het ad-einde aan. De duur van het `SpliceOut`-type van de `EXE-X-CUE`-markering kan nul zijn en het `SpliceIn`-type van `EXE-X-CUE`-markering markeert het einde van het ad-einde. Ze worden in één label weergegeven en verschillen per type.

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

In het ene markeerteken met verschillende typen voorbeeld, als de duur van het type `SpliceOut` nul is, moeten `SpliceOut` en `SpliceIn` voor elke advertentierak samenwerken. Momenteel is een `SpliceOut`-markering met een andere duur dan nul en hoeft u `SpliceIn`-markeertekens niet naast elkaar te plaatsen, meer standaard.

**Twee afzonderlijke markeringen**

Het meer typische scenario is een `SpliceOut` teller met een niet-nul duur en die niet de het in paren `SpliceIn` tellers nodig heeft. Hier markeert een koppelingsmarkering `SpliceIn` het einde van de advertentie tijdens het afspelen van een advertentie-einde, maar het ad-einde wordt kort geknipt op de markeerpositie `SpliceIn` en de hoofdinhoud wordt op deze positie afgespeeld.

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

