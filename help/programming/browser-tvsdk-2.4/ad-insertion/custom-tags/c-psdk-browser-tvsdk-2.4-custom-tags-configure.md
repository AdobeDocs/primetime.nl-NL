---
description: Mediastreams kunnen extra metagegevens bevatten in de vorm van tags in het MPD-bestand (Media Presentation Description). Dit bestand geeft de plaatsing van de reclame aan. U kunt aangepaste tagnamen opgeven en een melding ontvangen wanneer bepaalde tags in het manifestbestand worden weergegeven.
seo-description: Mediastreams kunnen extra metagegevens bevatten in de vorm van tags in het MPD-bestand (Media Presentation Description). Dit bestand geeft de plaatsing van de reclame aan. U kunt aangepaste tagnamen opgeven en een melding ontvangen wanneer bepaalde tags in het manifestbestand worden weergegeven.
seo-title: Aangepaste tags
title: Aangepaste tags
uuid: d1e34288-545b-440f-a262-2fb853f0e3c4
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Overzicht {#custom-tags-overview}

Mediastreams kunnen extra metagegevens bevatten in de vorm van tags in het MPD-bestand (Media Presentation Description). Dit bestand geeft de plaatsing van de reclame aan. U kunt aangepaste tagnamen opgeven en een melding ontvangen wanneer bepaalde tags in het manifestbestand worden weergegeven.

## HLS-inhoudscodes {#section_E99299152089418FBA56F5F09FC547B0}

>[!IMPORTANT]
>
>Deze functie is niet beschikbaar voor Safari op Apple-computers, omdat Browser-TVSDK de videotag gebruikt in plaats van Flash of MSE om HLS-inhoud af te spelen.

Browser TVSDK biedt offline ondersteuning voor specifieke #EXT-advertentietags. Uw toepassing kan aangepaste tags gebruiken om de publicatieworkflow te verbeteren of om uitvalscenario&#39;s te ondersteunen. Voor ondersteuning van geavanceerde workflows kunt u met Browser-TVSDK aanvullende tags in het manifest opgeven en hierop een abonnement nemen. U kunt op de hoogte worden gesteld wanneer deze labels in het manifestbestand worden weergegeven.

>[!TIP]
>
>U kunt zich abonneren op aangepaste tags voor zowel VOD- als live/lineaire streams.

>[!NOTE] {othertype=&quot;Beperking&quot;}
>
>Wanneer HLS wordt afgespeeld met de tag Video in Safari en niet met Flash Fallback, is deze functie niet beschikbaar in Safari.

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

* Een melding wanneer het bestand `#EXT-X-ASSET` tags bevat of een andere set aangepaste tagnamen waarop u een abonnement hebt genomen.
* Voeg advertenties in wanneer er een `#EXT-X-AD` tag of een andere aangepaste tagnaam in de stream wordt gevonden.

U kunt zich als aangepaste tags abonneren op een van de volgende tags: `EXT-PROGRAM-DATE-TIME`, `EXT-X-START`, `EXT-X-AD`, `EXT-X-CUE`, `EXT-X-ENDLIST`. Tijdens het parseren van manifestbestanden wordt u op de hoogte gesteld van een `TimedMetadata` gebeurtenis.

Er zijn enkele advertentietags, zoals `EXT-X-CUE`waarop u zich al hebt geabonneerd. Deze advertentietags worden ook gebruikt door de standaardopportuniteitsgenerator. U kunt opgeven welke advertentietags door de standaardopportuniteitsgenerator worden gebruikt door de `adTags` eigenschap in te stellen.

## DASH-inhoudtags {#section_967A952319BE4048B4C6612FFF7ADA6E}

DASH heeft twee manieren om gebeurtenissen te signaleren:

* In het MPD-bestand.

   Dit bestand lijkt op het M3U8-bestand in HLS-inhoud en het .mpd-bestand bevat MPD-gebeurtenissen.
* Inband in de weergave

   Inband gebeurtenissen worden met vertegenwoordiging vermenigvuldigd door de gebeurtenisberichten als deel van de segmenten toe te voegen. Een representatie is een lijst met video- en audiosegmenten die achtereenvolgens worden afgespeeld. De gegevens van de inband-gebeurtenis worden in deze segmenten ingesloten.

Deze gebeurtenissen worden als `TimedMetadata` gebeurtenissen aan de toepassing gemeld zodra ze door Browser TVSDK worden geparseerd. Zodra een gebeurtenis op de hoogte is gebracht, wordt deze niet opnieuw op de hoogte gesteld.
