---
description: Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.
title: Een vroege en eindresultaat implementeren
exl-id: 584e870e-1408-41a9-bb6f-e82b921fe99e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Een vroege en eindresultaat implementeren{#implementing-an-early-ad-break-return}

Voor live streaming en invoegen moet u mogelijk een ad-einde verlaten voordat alle advertenties in het einde worden afgespeeld.

>[!NOTE]
>
>Je moet je abonneren op de advertentiemarkeringen voor splice out/in ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`, en `#EXT-X-CUE`).

Hieronder volgen enkele vereisten die u in overweging wilt nemen:

* Parseermarkeringen zoals `EXT-X-CUE-IN` (of een equivalent markeringslabel) die worden weergegeven in de lineaire of FER-streams.

   Registreer de markeringen als de teller voor een vroege terugkeerpunt. Alleen afspelen `adBreaks` tot deze markeerpositie tijdens het afspelen, die de duur van de `adBreak` gemarkeerd door de regelafstand `EXE-X-CUE-OUT` markering.

* Indien twee `EXT-X-CUE-IN` er zijn markeringen voor dezelfde `EXT-X-CUE-OUT` markering, de eerste `EXT-X-CUE-IN` De markering die wordt weergegeven, telt.

* Als de `EXE-X-CUE-IN` markeerteken wordt in de tijdlijn weergegeven zonder regelafstand `EXT-X-CUE-OUT` markeerteken, de `EXE-X-CUE-IN` markering wordt genegeerd.

   In een live stream, als de regelafstand `EXT-X-CUE-OUT` De markering is net uit het venster verplaatst, de TVSDK reageert er niet op.

* Als er een vroege terugkeer van een advertentierammer is, `adBreak` wordt afgespeeld totdat de afspeelkop terugkeert naar de oorspronkelijke positie toen het ad-einde moest eindigen en het afspelen van de hoofdinhoud vanaf die positie wordt hervat.

## SpliceOut en SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` en `SpliceIn` markeertekens geven het begin en het einde van het ad-einde aan. De duur van de `SpliceOut` type `EXE-X-CUE` De markering is mogelijk nul en de `SpliceIn` type `EXE-X-CUE` markeerteken geeft het einde van het advertentieeinde aan. Ze worden in één label weergegeven en verschillen per type.

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

In de ene markering met verschillende typen bijvoorbeeld, als de duur van de `SpliceOut` tekst is nul, de `SpliceOut` en `SpliceIn` moeten samenwerken voor elke advertentie. Op dit moment is een `SpliceOut` markering met een duur die niet gelijk is aan nul en geen koppeling nodig heeft `SpliceIn` markeringen zijn meer typisch.

**Twee afzonderlijke markeringen**

Het meer typische scenario is een `SpliceOut` markering met een duur die niet gelijk is aan nul en waarvoor geen koppeling nodig is `SpliceIn` markeertekens. Hier, een bedrading `SpliceIn` markeert het einde van het advertentieeinde tijdens het afspelen van een advertentie-einde, maar het afbreking van de advertentie wordt kort bij het `SpliceIn` positie van de markering en de hoofdinhoud wordt op deze positie afgespeeld.

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
