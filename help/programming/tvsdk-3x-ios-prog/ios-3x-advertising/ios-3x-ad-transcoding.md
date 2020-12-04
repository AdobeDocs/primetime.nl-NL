---
description: Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video's.
seo-description: Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video's.
seo-title: Niet-compatibele advertenties opnieuw verpakken met de Adobe Creative Repackaging Service
title: Niet-compatibele advertenties opnieuw verpakken met de Adobe Creative Repackaging Service
uuid: 56a2405d-b395-4fea-820d-343590be7c19
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---


# Niet-compatibele advertenties opnieuw verpakken met de Adobe Creative Repackaging Service {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video&#39;s.

Advertenties die door verschillende derden worden aangeboden, zoals een bureau en server, uw inventarispartner of een advertentienetwerk, worden vaak in incompatibele indelingen geleverd, zoals MP4 met progressieve download.

Wanneer TVSDK voor het eerst een niet-compatibele advertentie tegenkomt, negeert de speler de advertentie en geeft een verzoek aan de creatieve herverpakkingsdienst (CRS) uit, die deel van Primetime en toevoegend achtereind uitmaakt, om de advertentie in een compatibel formaat te herverpakken. CRS probeert om met meerdere bitsnelheden M3U8-uitvoeringen van de advertentie te genereren en deze uitvoeringen op het netwerk voor de levering van primetime-inhoud (CDN) op te slaan. De volgende keer dat TVSDK een advertentierespons ontvangt die naar die advertentie wijst, gebruikt de speler de HLS-compatibele M3U8-versie van de CDN.

Neem contact op met uw Adobe als u deze optionele functie wilt inschakelen.

Zie [Creative Packaging Service (CRS)](../../../dynamic-ad-insertion/creative-repackaging-service/crs-overview.md) voor meer informatie over CRS.

## Meerdere CDN-ondersteuning voor CRS en levering {#section_900FDDA5454143718F1EB4C9732C8E1C}

Terwijl het standaard Creative Repackaging Service (CRS)-scenario één Content Data Network (CDN) moet gebruiken, kunt u de CRS-elementen op meerdere CDN&#39;s implementeren.

U kunt meerdere CDN&#39;s gebruiken om de volgende redenen:

* Een vereiste om groter te worden voor grote het bekijken gebeurtenissen.
* Een vereiste om de CDN-bron van het CRS-element te koppelen aan de CDN-bron van de hoofdinhoud.

U kunt de standaard-URL die door het CRS wordt geleverd, transformeren met TVSDK URL Transformer-API&#39;s.

Hier volgen de API-toevoegingen in TVSDK:

* `PTURLTransformer` Een protocol dat de methodes beschrijft die worden vereist om CRS en URLs om te zetten die door TVSDK worden gevraagd. De toepassingen kunnen dit protocol uitvoeren en implementaties voor de vereiste methodes verstrekken.

* `PTDefaultURLTransformer` De standaardobformatie URL die in TVSDK wordt gecreeerd en die het  `PTURLTransformer` protocol uitvoert. Toepassingen kunnen deze klasse overschrijven of een post-URL-transformatiehandler toevoegen. Deze handler is nuttig wanneer de toepassing wijzigingen in het URL-verzoek wil aanbrengen nadat de standaardtransformatie is toegepast.

* `PTNetworkConfiguration setURLTransformer:defaultTransformer` Een settermethode die op de  `PTNetworkConfiguration` meta-gegevensinstantie wordt verstrekt om de  `PTURLTransformer` implementatie te plaatsen.

>[!IMPORTANT]
>
>Uw app-implementaties moeten de opsomming `PTURLTransformerInputType` controleren en alleen URL&#39;s van het type `PTURLTransformerInputTypeCRSCreative` voor CRS transformeren.

In het volgende codevoorbeeld ziet u hoe uw toepassing de standaardhostcomponent in een andere tekenreeks kan wijzigen (bijvoorbeeld `cdn.mycrsdomain.com`):

```
// The sample code below uses Non-ARC code 
PTNetworkConfiguration *networkConfiguration = [[[PTNetworkConfiguration alloc] init] autorelease]; 
   
PTDefaultURLTransformer *defaultTransformer = [[[PTDefaultURLTransformer alloc] init] autorelease]; 
    [defaultTransformer addPostURLTransformHandler:^NSString *(NSString *url, PTURLTransformerInputType type) { 
        if (type == PTURLTransformerInputTypeCRSCreative) { 
            return [url stringByReplacingOccurrencesOfString:[NSURL URLWithString:url].host  
              withString:@"cdn.mycrsdomain.com"]; 
        } 
            return url; 
    }]; 
  
[networkConfiguration setURLTransformer:defaultTransformer]; 
   
// metadata is the PTMetadata instance set on a PTMediaPlayerItem instance. 
[metadata setMetadata:[self getNetworkConfiguration] forKey:PTNetworkConfigurationMetadataKey];
```
