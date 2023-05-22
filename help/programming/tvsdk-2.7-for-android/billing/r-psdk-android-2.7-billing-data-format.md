---
description: TVSDK verzendt factureringsmetriek naar Adobe in een formaat van XML.
title: Factureringsgegevens verzenden
exl-id: 5f42d032-cd2c-4e5e-8960-db555ba75626
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# Factureringsgegevens verzenden {#transmit-billing-metrics}

TVSDK verzendt factureringsmetriek naar Adobe in een formaat van XML.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Als u een netwerk vangt hulpmiddel gebruikt om de statistiekenTVSDK te controleren brengt naar Adobe over, zou u eenheden als het volgende moeten zien:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<request>
    <sc_xml_ver>1.0</sc_xml_ver>
    <reportSuiteID>primesample2</reportSuiteID>
    <visitorID>947310128cb56f41</visitorID>
    <pageURL>https://. . ..m3u8</pageURL>
    <timestamp>2016-4-7T10:1:4</timestamp>
    <contextData>
        <billingMetrics>
            <publisherID>com.adobe.primetime.reference.PrimetimeReference</publisherID>
            <contentType>vod</contentType>
            <adsEnabled>true</adsEnabled>
            <midrollEnabled>true</midrollEnabled>
            <platform>Mac OSX 10.11.5</platform>
            <tvsdkVersion>2,4,0,1559</tvsdkVersion>
            <contentURL>https://. . ..m3u8</contentURL>
        </billingMetrics>
    </contextData>
</request>
```

Booleaanse eigenschappen `drmProtected`, `adsEnabled`, en `midrollEnabled` worden alleen weergegeven als ze waar zijn.
