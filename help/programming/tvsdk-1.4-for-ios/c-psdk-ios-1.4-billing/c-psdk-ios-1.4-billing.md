---
description: Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek verzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.
seo-description: Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek verzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.
seo-title: Factureringscijfers
title: Factureringscijfers
uuid: 658ffbcd-dedc-464c-8ec7-aa3bdfcb1512
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# Factureringscijfers {#billing-metrics}

Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek verzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.

Telkens wanneer de speler een streamstartgebeurtenis genereert, begint TVSDK regelmatig HTTP-berichten naar het Adobe systeem te verzenden. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de werkelijke waarden.

De berichten bevatten de volgende informatie:

* Inhoudstype (live, lineair of VOD)
* Inhoud-URL
* Of advertenties zijn ingeschakeld
* Of mid-roll-advertenties zijn ingeschakeld (alleen VOD)
* Of de stream door DRM is beveiligd
* De TVSDK-versie en -platform

Adobe configureert deze indeling vooraf, maar als u de indeling wilt wijzigen, werkt u samen met uw Adobe Enablement-vertegenwoordiger.

Om de statistieken te controleren die TVSDK naar Adobe verzendt, verkrijg URL van uw vertegenwoordiger van Inablement van de Adobe, en gebruik een netwerk vangt hulpmiddel, bijvoorbeeld, Charles, om de gegevens te zien.

## Factureringsmetriek {#configure-billing-metrics} vormen

Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw Adobe Enablement vertegenwoordiger hebt verkregen, gebruik de klasse PTBillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.

De meeste klanten zouden de standaardconfiguratie moeten gebruiken.

>[!IMPORTANT]
>
>De configuratie die u instelt, blijft van kracht gedurende de levensduur van de mediaspeler. Nadat u de mediaspeler hebt geïnitialiseerd, kunt u de configuratie niet meer wijzigen.

Factureringsmetriek vormen:

1. Voer het volgende codevoorbeeld in.

   ```
   PTBillingMetricsConfiguration *billingConfig = [[[PTBillingMetricsConfiguration alloc] init] autorelease]; 
   billingConfig.enabled = YES; 
   billingConfig.stdVODBillableDurationMinutes = 60.0; 
   billingConfig.proVODBillableDurationMinutes = 30.0; 
   billingConfig.liveBillableDurationMinutes = 15.0; 
   
   // metadata is the PTMetadata instance set on PTMediaPlayerItem 
   [metadata setMetadata:billingConfig forKey:PTBillingMetricsConfigurationMetadataKey];
   ```

## Factureringscijfers {#transmit-billing-metrics} verzenden

TVSDK verzendt factureringsmetriek naar Adobe in een formaat van XML.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Als u een netwerk vangt hulpmiddel gebruikt om de statistiekenTVSDK te controleren brengt naar Adobe over, zou u eenheden als het volgende moeten zien:

```
<request> 
     <sc_xml_ver>1.0</sc_xml_ver> 
     <reportSuiteID>ptebilling</reportSuiteID> 
     <visitorID>5536C629-5EF7-4F02-8E5D-9FA136CB3CED</visitorID> 
     <pageName>com.adobe.primetime.psdksample</pageName> 
     <timestamp>2016-11-22T18:06:30+0000</timestamp> 
     <userAgent>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</userAgent> 
     <contextData> 
         <billingMetrics> 
                 <contentDuration>1799111</contentDuration> 
                 <contentURL>https%3A%2F%2Fdevimages.apple.com.edgekey.net%2Fstreaming%2Fexamples%2Fbipbop_16x9%2Fbipbop_16x9_variant.m3u8</contentURL> 
                 <contentType>vod</contentType> 
                 <midrollEnabled>true</midrollEnabled> 
                 <tvsdkVersion>1.0.211</tvsdkVersion> 
                 <platform>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</platform> 
                 <publisherID>com.adobe.primetime.psdksample</publisherID> 
                 <adsEnabled>true</adsEnabled> 
                 <type>start</type> 
         </billingMetrics> 
     </contextData> 
</request>
```

De booleaanse eigenschappen `drmProtected`, `adsEnabled` en `midrollEnabled` worden alleen weergegeven als ze waar zijn.