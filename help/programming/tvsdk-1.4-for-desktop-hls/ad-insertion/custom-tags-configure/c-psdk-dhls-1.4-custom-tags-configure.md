---
description: Mediastreams kunnen aanvullende metagegevens in de vorm van tags in het bestand playlist/manifest bevatten. Dit bestand geeft de plaatsing van de reclame aan. U kunt aangepaste tagnamen opgeven en een melding ontvangen wanneer bepaalde tags in het manifestbestand worden weergegeven.
title: Aangepaste tags
exl-id: 1b660b2a-c48b-49f9-af14-8b2318119e9a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Aangepaste tags{#custom-tags}

Mediastreams kunnen aanvullende metagegevens in de vorm van tags in het bestand playlist/manifest bevatten. Dit bestand geeft de plaatsing van de reclame aan. U kunt aangepaste tagnamen opgeven en een melding ontvangen wanneer bepaalde tags in het manifestbestand worden weergegeven.

## HLS-inhoudscodes {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Deze functie is niet beschikbaar voor Safari op Apple-computers, omdat TVSDK de videotag gebruikt in plaats van Flash of MSE om HLS-inhoud af te spelen.

TVSDK biedt offline ondersteuning voor specifieke #EXT-advertentietags. Uw toepassing kan aangepaste tags gebruiken om de publicatieworkflow te verbeteren of om uitvalscenario&#39;s te ondersteunen. Voor ondersteuning van geavanceerde workflows kunt u met TVSDK aanvullende tags in het manifest opgeven en hierop een abonnement nemen. U kunt op de hoogte worden gesteld wanneer deze labels in het manifestbestand worden weergegeven.

>[!TIP]
>
>U kunt zich abonneren op aangepaste tags voor zowel VOD- als live/lineaire streams.

>[!NOTE]
>
>Wanneer HLS door de Video markering in Safari, en niet door Flash Fallback te gebruiken wordt gespeeld, zal deze eigenschap niet beschikbaar in Safari zijn.

## Aangepaste HLS-tags gebruiken {#section_AD032318AEF5418393D2B1DF36B0BABB}

Hier volgt een voorbeeld van een aangepast VOD-element:

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Uw toepassing kan de volgende scenario&#39;s instellen:

* Een melding wanneer `#EXT-X-ASSET` -tags of een andere set aangepaste tagnamen waarop u zich hebt geabonneerd, bestaan in het bestand.
* Advertenties invoegen wanneer een `#EXT-X-AD` -tag of een andere aangepaste tagnaam in de stream wordt gevonden.

U kunt zich als aangepaste tags abonneren op een van de volgende tags: `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. U wordt op de hoogte gesteld van een `TimedMetadata` gebeurtenis tijdens het parseren van manifestbestanden.

Er zijn enkele advertentietags, zoals `EXT-X-CUE`, waarop u al bent geabonneerd. Deze advertentietags worden ook gebruikt door de standaardopportuniteitsgenerator. U kunt opgeven welke advertentietags door de standaardopportuniteitsgenerator worden gebruikt door de optie `adTags` eigenschap.
