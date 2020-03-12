---
description: Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video's.
seo-description: Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video's.
seo-title: Niet-compatibele advertenties opnieuw verpakken met Adobe Creative Repackaging Service
title: Niet-compatibele advertenties opnieuw verpakken met Adobe Creative Repackaging Service
uuid: 3bc24185-6b19-4660-bf78-5ccdaf14787a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Niet-compatibele advertenties opnieuw verpakken met Adobe Creative Repackaging Service {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video&#39;s.

Advertenties die door verschillende derden worden aangeboden, zoals een bureau en server, uw inventarispartner of een advertentienetwerk, worden vaak in incompatibele indelingen geleverd, zoals MP4 met progressieve download.

Wanneer TVSDK voor het eerst een niet-compatibele advertentie tegenkomt, negeert de speler de advertentie en geeft een verzoek aan de creatieve herverpakkingsdienst (CRS) uit, die deel van Primetime en toevoegend achtereind uitmaakt, om de advertentie in een compatibel formaat te herverpakken. CRS probeert om met meerdere bitsnelheden M3U8-uitvoeringen van de advertentie te genereren en deze uitvoeringen op het netwerk voor de levering van primetime-inhoud (CDN) op te slaan. De volgende keer dat TVSDK een advertentierespons ontvangt die naar die advertentie wijst, gebruikt de speler de HLS-compatibele M3U8-versie van de CDN.

Neem contact op met uw vertegenwoordiger van Adobe om deze optionele functie in te schakelen.

Voor meer informatie over CRS, zie de Dienst van het [Verpakken Creative (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## Meerdere CDN-ondersteuning voor CRS en levering {#multiple-cdn-support-for-crs-ad-delivery}

Terwijl het standaard Creative Repackaging Service (CRS)-scenario één Content Data Network (CDN) moet gebruiken, kunt u de CRS-elementen op meerdere CDN&#39;s implementeren.

U kunt meerdere CDN&#39;s gebruiken om de volgende redenen:

* Een vereiste om groter te worden voor grote het bekijken gebeurtenissen.
* Een vereiste om de CDN-bron van het CRS-element te koppelen aan de CDN-bron van de hoofdinhoud.

U kunt de standaard-URL die door het CRS wordt geleverd, transformeren met TVSDK URL Transformer-API&#39;s.

Hier volgen de API-toevoegingen in TVSDK:

* `URLTransformer` An interface that describes the methods that are required to transform the CRS and URLs that are requested by TVSDK. De toepassingen kunnen deze interface uitvoeren en implementaties voor de vereiste methodes verstrekken.

* `DefaultURLTransformer` De standaardinstantie van de transformator URL die in TVSDK wordt gecreeerd en die de `URLTransformer` interface uitvoert. Toepassingen kunnen deze klasse overschrijven of een post-URL-transformatiehandler toevoegen. Deze handler is nuttig wanneer de toepassing wijzigingen in het URL-verzoek wil aanbrengen nadat de standaardtransformatie is toegepast.

* `NetworkConfiguration.urlTransformer` Een settermethode die op de `NetworkConfiguration` metagegevensinstantie wordt opgegeven om de `URLTransformer` implementatie in te stellen.

>[!IMPORTANT]
>
>Uw app-implementaties moeten de opsomming controleren en alleen URL&#39;s van het type `URLTransformerInputType` `URLTransformerInputType.CRSCreative` voor CRS transformeren.

In het volgende codevoorbeeld ziet u hoe uw toepassing de standaardhostcomponent kan wijzigen in een andere tekenreeks (bijvoorbeeld `cdn.mycrsdomain.com`):

```
var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   
var urlTransformer:DefaultURLTransformer = new DefaultURLTransformer(); 
urlTransformer.addPostURLTransformHandler(function (url:String, type:String) { 
    if (type == URLTransformerInputType.CRSCreative) { 
        return url.replace(URLUtil.getServerName(url), "cdn.mycrsdomain.com"); 
    } 
    return url; 
}); 
  
networkConfiguration.urlTransformer = urlTransformer; 
   
// metadata is the Metadata instance set on a MediaResource instance. 
metadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                     networkConfiguration);
```
