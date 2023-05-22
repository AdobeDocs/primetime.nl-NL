---
description: Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.
title: Extra fallback voor VAST- en VMAP-advertenties
exl-id: 6575c08f-3a6a-4de5-b333-bceabbe00460
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Extra fallback voor VAST- en VMAP-advertenties {#ad-fallback-for-vast-and-vmap-ads}

Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.

In de VAST/Digital Video Multiple Ad Playlist (VMAP)-specificatie staat dat voor advertenties waarvoor VAST-fallback is ingeschakeld, lege advertenties automatisch het gebruik van fallback-advertenties activeren. Als een VAST-advertentie leeg is, zoekt TVSDK naar een geldige vervanging van het HLS-mediatype in de fallback-advertenties. Als een VAST-advertentie in een omslag een ongeldig mediatype heeft, behandelt TVSDK deze advertentie als leeg. U kunt configureren of TVSDK hetzelfde moet doen voor inline-advertenties in een VMAP. Voor meer informatie over de VAST `fallbackOnNoAd` functie, zie [Digital Video Ad Serving Template (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

## Definieer de fallback en het gedrag voor inline VMAP-advertenties {#define-fallback-ad-behavior-for-vmap-inline-ads}

U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.

1. Set `fallbackOnInvalidCreative` naar waar om VMAP terug te vallen wanneer het media type voor lineair/gealigneerd en voor HLS ongeldig is.

   De standaardwaarde is false. Als een lineaire advertentie mislukt omdat deze een ongeldig mediatype heeft of omdat de advertentie niet opnieuw kan worden verpakt, staat deze markering toe dat Primetime en het besluit hetzelfde fallback-gedrag volgen als wanneer de advertentie een lege VAST-wrapper was.

   ```
   var auditudeMetadata:AuditudeSettings = new AuditudeSettings(); 
   auditudeMetadata.fallbackOnInvalidCreative = true;
   ```

## Extra fallback-gedrag voor VAST en VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Wanneer Primetime en besluitvorming een VAST-advertentie (creatief) tegenkomen die leeg is of een mediatype heeft dat ongeldig is voor HLS, worden de fallback-advertenties geëvalueerd om te bepalen wat er moet worden geretourneerd.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

In TVSDK zijn de enige geldige mediatypen: `application/x-shockwave-flash` (VPAID) en `application/x-mpegURL` (m3u8).

Wanneer er stand-alone reserveadvertenties zijn, zoekt de Insteekmodule Primetime en het besluit deze advertenties in de volgende orde en keert de eerste advertentie met een geldig media type terug:

1. Als het opnieuw verpakken is ingeschakeld, wordt het eerste exemplaar van een advertentie met een ongeldig mediatype behandeld als andere ongeldige mediatypen.

   Als het opnieuw verpakken mislukt, is dit proces van toepassing op andere exemplaren van de advertentie.
1. Als TVSDK geen geldige fallback-advertenties vindt, wordt de oorspronkelijke advertentie met het ongeldige mediatype geretourneerd.
1. Als een fallback-advertentie met een geldig MIME-type wordt geretourneerd in plaats van de originele advertentie, verzenden Primetime en het nemen van beslissingen foutcode 403 naar de VAST-fout-URL, indien beschikbaar.
1. Als een fallback-advertentie een omslag is en meerdere advertenties retourneert, worden alleen advertenties met het juiste mediatype geretourneerd.

>[!IMPORTANT]
>
>Dit gedrag is altijd ingeschakeld voor advertenties in VAST-wrappers. Voor VAST-advertenties inline in een VMAP is het gedrag standaard uitgeschakeld, maar uw toepassing kan dit gedrag wel inschakelen.
