---
description: Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.
seo-description: Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.
seo-title: Extra fallback voor VAST- en VMAP-advertenties
title: Extra fallback voor VAST- en VMAP-advertenties
uuid: ca65f349-012d-49e3-8c23-fd041c5362ee
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---


# Extra fallback voor VAST- en VMAP-advertenties {#ad-fallback-for-vast-and-vmap-ads}

Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.

In de VAST/Digital Video Multiple Ad Playlist (VMAP)-specificatie staat dat voor advertenties waarvoor VAST-fallback is ingeschakeld, lege advertenties automatisch het gebruik van fallback-advertenties activeren. Als een VAST-advertentie leeg is, zoekt TVSDK naar een geldige vervanging van het HLS-mediatype in de fallback-advertenties. Als een VAST-advertentie in een omslag een ongeldig mediatype heeft, behandelt TVSDK deze advertentie als leeg. U kunt configureren of TVSDK hetzelfde moet doen voor inline-advertenties in een VMAP. Zie [Digital Video Ad Serving Template (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast) voor meer informatie over de functie VAST `fallbackOnNoAd`.

## Definieer fallback en gedrag voor inline VMAP-advertenties {#section_D90BB3C6E539472EABF000C0F616DBE2}

U kunt fallback inschakelen wanneer een inline VMAP-bestand een ongeldig mediatype bevat.

1. Stel `FallbackOnInvalidCreativeEnabled` in op `YES` om VMAP terug te laten vallen wanneer het mediatype voor een lineaire/inline-advertentie ongeldig is voor HLS.

   >[!NOTE]
   >
   >De standaardwaarde is NO. Als een lineaire advertentie mislukt omdat deze een ongeldig mediatype heeft of omdat de advertentie niet opnieuw kan worden verpakt, staat deze markering toe dat Primetime en het besluit hetzelfde fallback-gedrag volgen als wanneer de advertentie een lege VAST-wrapper was.

   ```
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.isFallbackOnInvalidCreativeEnabled = YES;
   ```

## Extra fallbackgedrag voor VAST en VMAP {#section_5B6716CC49CC4C40964CFE9F122C57A6}

Wanneer Primetime en besluitvorming een VAST-advertentie (creatief) tegenkomen die leeg is of een mediatype heeft dat ongeldig is voor HLS, worden de fallback-advertenties geëvalueerd om te bepalen wat er moet worden geretourneerd.

In TVSDK is het enige geldige mediatype `application/x-mpegURL` (M3U8).

Wanneer er stand-alone reserveadvertenties zijn, zoekt de Insteekmodule Primetime en het besluit deze advertenties in de volgende orde en keert de eerste advertentie met een geldig media type terug:

1. Als het opnieuw verpakken is ingeschakeld, wordt het eerste exemplaar van een advertentie met een ongeldig mediatype behandeld als andere ongeldige mediatypen.

   Als het opnieuw verpakken mislukt, is dit proces van toepassing op andere exemplaren van de advertentie.
1. Als TVSDK geen geldige fallback-advertenties vindt, wordt de oorspronkelijke advertentie met het ongeldige mediatype geretourneerd.
1. Als een fallback-advertentie met een geldig MIME-type wordt geretourneerd in plaats van de originele advertentie, verzenden Primetime en het nemen van beslissingen foutcode 403 naar de VAST-fout-URL, indien beschikbaar.
1. Als een fallback-advertentie een omslag is en meerdere advertenties retourneert, worden alleen advertenties met het juiste mediatype geretourneerd.

>[!IMPORTANT]
>
>Dit gedrag is altijd ingeschakeld voor advertenties in VAST-wrappers. Voor VAST-advertenties inline in een VMAP is het gedrag standaard uitgeschakeld, maar uw toepassing kan dit gedrag wel inschakelen.