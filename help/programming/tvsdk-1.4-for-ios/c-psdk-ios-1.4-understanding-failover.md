---
description: Failover-afhandeling treedt op wanneer een afspeellijst van een variant meerdere uitvoeringen voor dezelfde bitsnelheid heeft en een van de uitvoeringen niet meer werkt. De TVSDK wisselt tussen uitvoeringen.
seo-description: Failover-afhandeling treedt op wanneer een afspeellijst van een variant meerdere uitvoeringen voor dezelfde bitsnelheid heeft en een van de uitvoeringen niet meer werkt. De TVSDK wisselt tussen uitvoeringen.
seo-title: Failover
title: Failover
uuid: 53cf611f-59e6-4728-a287-b98907d7f7bb
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---


# Failover{#failover}

Failover-afhandeling treedt op wanneer een afspeellijst van een variant meerdere uitvoeringen voor dezelfde bitsnelheid heeft en een van de uitvoeringen niet meer werkt. De TVSDK wisselt tussen uitvoeringen.

Het volgende voorbeeld toont een variant playlist met failover URLs van het zelfde beetjetarief:

```
#EXTM3U
#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8090/_default_/_default_/livestream.m3u8   

#EXT-X-STREAM-INF:PROGRAM-ID=1, BANDWIDTH =700000
https://sj2slu225.corp.adobe.com:8091/_default_/_default_/livestream.m3u8
```

Wanneer TVSDK de afspeellijst met varianten laadt, wordt er een wachtrij gemaakt met de URL&#39;s voor alle uitvoeringen van de inhoud voor dezelfde bitsnelheid. Wanneer een verzoek om een URL ontbreekt, gebruikt TVSDK volgende URL van het zelfde beetjetarief van de failoverrij. Op elk specifiek mislukkingstijdstip doorloopt TVSDK één keer alle beschikbare URL&#39;s tot het een URL vindt die correct werkt of tot het alle beschikbare URL&#39;s heeft geprobeerd. Als TVSDK heeft geprobeerd alle beschikbare URL&#39;s te gebruiken en geen van de URL&#39;s werkt, probeert TVSDK de inhoud niet meer af te spelen.

Failover treedt alleen op M3U8-niveau op, wat betekent:

* Voor VOD, kan failover slechts voorkomen wanneer het begint te proberen om te spelen en niet nadat het is begonnen te spelen.
* Bij live streaming kan failover plaatsvinden in het midden van de stream.

>[!TIP]
>
>TVSDK, in plaats van de Apple AV Foundation-speler, biedt failover-verwerking.

