---
description: Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.
seo-description: Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.
seo-title: Factureringsgebruiksmaatstaven
title: Factureringsgebruiksmaatstaven
uuid: e792cc72-b1ae-42ce-8b71-f9f9f1de0614
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Factureringscijfers {#billing-metrics}

Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.

Telkens wanneer de speler een streamstartgebeurtenis genereert, verzendt TVSDK regelmatig HTTP-berichten naar het factureringssysteem van Adobe. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de werkelijke waarden.

De berichten bevatten de volgende informatie:

* Inhoudstype (live, lineair of VOD)
* Inhoud-URL
* Of advertenties zijn ingeschakeld
* Of mid-roll-advertenties zijn ingeschakeld (alleen VOD)
* Of de stream door DRM is beveiligd
* De TVSDK-versie en -platform

Adobe configureert deze indeling vooraf, maar als u de rangschikking wilt wijzigen, werkt u samen met uw Adobe Enablement-vertegenwoordiger.

Als u de statistieken wilt controleren die TVSDK naar Adobe verzendt, vraagt u de URL bij uw Adobe Enablement-vertegenwoordiger en gebruikt u een hulpprogramma voor het vastleggen van netwerken, bijvoorbeeld Charles, om de gegevens te bekijken.

## Factureringsmetriek configureren {#configure-billing-metrics}

Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters hebt gekregen van uw Adobe Enablement-vertegenwoordiger, gebruikt u de klasse PTBillingMetricsConfiguration om deze parameters in te stellen voordat u de mediaspeler initialiseert.

De meeste klanten zouden de standaardconfiguratie moeten gebruiken.

>[!IMPORTANT]
>
>De configuratie die u instelt, blijft van kracht gedurende de levensduur van de mediaspeler. Nadat u de mediaspeler hebt geïnitialiseerd, kunt u de configuratie niet meer wijzigen.

Factureringsmetriek vormen:

Voer het volgende codevoorbeeld in.

```
PTBillingMetricsConfiguration *billingConfig = [[[PTBillingMetricsConfiguration alloc] init] autorelease]; 
billingConfig.enabled = YES; 
billingConfig.stdVODBillableDurationMinutes = 60.0; 
billingConfig.proVODBillableDurationMinutes = 30.0; 
billingConfig.liveBillableDurationMinutes = 15.0; 
                
// metadata is the PTMetadata instance set on PTMediaPlayerItem 
[metadata setMetadata:billingConfig forKey:PTBillingMetricsConfigurationMetadataKey];
```

## Factureringsgegevens verzenden {#transmit-billing-metrics}

TVSDK verzendt factuurgegevens naar Adobe in XML-indeling.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Als u een hulpprogramma voor het vastleggen van netwerken gebruikt om de statistieken te controleren die TVSDK naar Adobe verzendt, ziet u bijvoorbeeld de volgende eenheden:

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

De booleaanse eigenschappen `drmProtected`, `adsEnabled`en `midrollEnabled` worden alleen weergegeven als ze waar zijn.