---
description: Vervang een VOD-tijdlijn door een nieuw verzoek tot invoeging naar de manifestserver te verzenden met een correct ingestelde tijdlijnqueryparameter.
title: Een VOD-tijdlijn vervangen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Een VOD-tijdlijn {#replace-a-vod-timeline} vervangen

Vervang een VOD-tijdlijn door een nieuw verzoek tot invoeging naar de manifestserver te verzenden met een correct ingestelde tijdlijnqueryparameter.

1. Bereid een verzoek tot toevoeging van een advertentie op de gebruikelijke manier voor.
1. Plaats de `ptcueformat` vraagparameter aan DPIScte35.
1. Stel de query-parameter `enableC3` in op true of false zoals van toepassing.
1. Maak een parameter `pttimeline` met de tijdlijnindeling VOD:
   1. Geef elk inhoudsblok (hoofdstuk) op met `duration = 0` en `number_of_lots = 1`.
   1. Geef elk advertentieblok op zoals gewoonlijk, maar stel `lots = 0` in om een einde te verwijderen. Stel `duration = 0` in om de duur van het ad-einde te gebruiken (uit het M3U8-bestand).

## Voorbeeld: Een VOD-tijdlijn vervangen

In dit voorbeeld wordt ervan uitgegaan dat de VOD-inhoud zich in `Original.m3u8` met een tijdlijn van `C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;` bevindt

Het volgende manifestserververzoek vervangt de onderbrekingen in `Original.m3u8` met een pre-rol 30 seconden, gevolgd door twee onderbrekingen van duur twee minuten elk.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

Het volgende manifestserververzoek verwijdert de onderbrekingen in `Original.m3u8` en voegt een pre-rol 30 seconden en een post-rol 30 toe.

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
