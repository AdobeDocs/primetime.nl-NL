---
description: Vervang een VOD-tijdlijn door een nieuw verzoek tot invoeging naar de manifestserver te verzenden met een correct ingestelde tijdlijnqueryparameter.
title: Een VOD-tijdlijn vervangen
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Een VOD-tijdlijn vervangen {#replace-a-vod-timeline}

Vervang een VOD-tijdlijn door een nieuw verzoek tot invoeging naar de manifestserver te verzenden met een correct ingestelde tijdlijnqueryparameter.

1. Bereid een verzoek tot toevoeging van een advertentie op de gebruikelijke manier voor.
1. Stel de `ptcueformat` queryparameter voor DPIScte35.
1. Stel de `enableC3` queryparameter naar waar of onwaar (true).
1. Een `pttimeline` parameter met de tijdlijnnotatie VOD:
   1. Geef elk inhoudsblok (hoofdstuk) op met `duration = 0` en `number_of_lots = 1`.
   1. Geef elk blok advertentie op zoals gewoonlijk, maar stel `lots = 0` om een einde te verwijderen. Set `duration = 0` om de duur van het ad-einde te gebruiken (uit het M3U8-bestand).

## Voorbeeld: Een VOD-tijdlijn vervangen

In dit voorbeeld wordt ervan uitgegaan dat de VOD-inhoud zich in `Original.m3u8` met een tijdlijn van `C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;`

Het volgende manifestserververzoek vervangt de onderbrekingen in `Original.m3u8` met een voorrol van 30 seconden, gevolgd door twee pauzes van telkens twee minuten.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

Het volgende manifestserververzoek verwijdert de onderbrekingen in `Original.m3u8` en voegt een voorrol van 30 seconden en een post-rol van 30 seconden toe.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
