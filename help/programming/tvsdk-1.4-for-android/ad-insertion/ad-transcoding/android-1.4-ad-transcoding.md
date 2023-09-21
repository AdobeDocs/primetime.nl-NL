---
description: Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video's.
title: Niet-compatibele advertenties opnieuw verpakken met de Adobe Creative Repackaging Service
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Niet-compatibele advertenties opnieuw verpakken met de Adobe Creative Repackaging Service {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video&#39;s.

Advertenties die door verschillende derden worden aangeboden, zoals een bureau en server, uw inventarispartner of een advertentienetwerk, worden vaak in incompatibele indelingen geleverd, zoals MP4 met progressieve download.

Wanneer TVSDK voor het eerst een niet-compatibele advertentie tegenkomt, negeert de speler de advertentie en geeft een verzoek aan de creatieve herverpakkingsdienst (CRS) uit, die deel van Primetime en toevoegend achtereind uitmaakt, om de advertentie in een compatibel formaat te herverpakken. CRS probeert om met meerdere bitsnelheden M3U8-uitvoeringen van de advertentie te genereren en deze uitvoeringen op het netwerk voor de levering van primetime-inhoud (CDN) op te slaan. De volgende keer dat TVSDK een advertentierespons ontvangt die naar die advertentie wijst, gebruikt de speler de HLS-compatibele M3U8-versie van de CDN.

Neem contact op met uw Adobe als u deze optionele functie wilt inschakelen.

Voor meer informatie over CRS, zie [Creative Packaging Service (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## Meerdere CDN-ondersteuning voor CRS en levering{#multiple-cdn-support-for-crs-ad-delivery}

Terwijl het standaard Creative Repackaging Service (CRS)-scenario één Content Data Network (CDN) moet gebruiken, kunt u de CRS-elementen op meerdere CDN&#39;s implementeren.

U kunt meerdere CDN&#39;s gebruiken om de volgende redenen:

* Een vereiste om groter te worden voor grote het bekijken gebeurtenissen.
* Een vereiste om de CDN-bron van het CRS-element te koppelen aan de CDN-bron van de hoofdinhoud.

U kunt de standaard-URL die door het CRS wordt geleverd, transformeren met TVSDK URL Transformer-API&#39;s.

Hier volgen de API-toevoegingen in TVSDK:

* `URLTransformer` An interface that describes the methods that are required to transform the CRS and URLs that are requested by TVSDK. De toepassingen kunnen deze interface uitvoeren en implementaties voor de vereiste methodes verstrekken.

* `DefaultURLTransformer` De standaardoperator voor URL-transformatie die in TVSDK is gemaakt en die het `URLTransformer` interface. Toepassingen kunnen deze klasse overschrijven of een post-URL-transformatiehandler toevoegen. Deze handler is nuttig wanneer de toepassing wijzigingen in het URL-verzoek wil aanbrengen nadat de standaardtransformatie is toegepast.

* `NetworkConfiguration.setURLTransformer` Een settermethode die op de `NetworkConfiguration` instantie van metagegevens die moet worden ingesteld `URLTransformer` uitvoering.

>[!IMPORTANT]
>
>Uw app-implementaties moeten controleren op de `URLTransformerInputType` opsomming en alleen transformatie-URL&#39;s van het type `URLTransformerInputType.CRSCreative` voor CRS.

In het volgende codevoorbeeld ziet u hoe uw toepassing de standaardhostcomponent in een andere tekenreeks kan wijzigen (bijvoorbeeld `cdn.mycrsdomain.com`):

```java
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
DefaultURLTransformer urlTransformer = new DefaultURLTransformer(); 
urlTransformer.addPostURLTransformHandler(new DefaultURLTransformer.URLTransformHandler() { 
    @Override 
    public String call(String url, URLTransformerInputType type) { 
        if (type == URLTransformerInputType.CRSCreative) { 
            try { 
                return url.replaceAll(new java.net.URI(url).getHost(), "cdn.mycrsdomain.com"); 
            } catch (URISyntaxException e) { 
            } 
        } 
        return url; 
    } 
}); 
   
networkConfiguration.setURLTransformer(urlTransformer); 
   
// metadata is the Metadata instance set on a MediaResource instance. 
metadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(), networkConfiguration);
```
