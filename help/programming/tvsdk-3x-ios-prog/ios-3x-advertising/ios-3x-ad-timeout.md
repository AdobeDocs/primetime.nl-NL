---
description: U kunt advertenties in uw VOD en levende/lineaire inhoud opnemen door Adobe Primetime en besluitvormingsinterface te gebruiken.
seo-description: U kunt advertenties in uw VOD en levende/lineaire inhoud opnemen door Adobe Primetime en besluitvormingsinterface te gebruiken.
seo-title: Reclamevereisten
title: Reclamevereisten
uuid: 0287f1e4-746f-42e5-b811-409064dd9b13
translation-type: tm+mt
source-git-commit: 48ad8aad89701f8414e752a4d4e41da252d28d62
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Time-out toevoegen {#ad-timeout}

## AV Foundation-vereisten {#av-foundation-requirements}

In het geval van VOD-inhoud moet het naaien van de afspeellijst, waarbij het laden van het hoofdinhoudsmanifest en het laden van de resolutie en het ad-manifest worden doorlopen, binnen 35 seconden worden voltooid.

In het geval van Live-inhoud moet u de afspeellijst na elke update binnen 20 seconden bijwerken.

**API&#39;s die relevant zijn voor de time-out voor AdResolution**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

U kunt addResolutionTimeout instellen door PTAdMetadata::adResolutionTimeout in te stellen bij het instellen van de metagegevens van uw advertentie.

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

Hierna volgt u de rubriek: [Metagegevens van primetime en server](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).

**API&#39;s die relevant zijn voor AdManifest Timeout**

```
/** @name Properties */
 /** The default timeout value (in seconds) for loading of ad manifests is 5 seconds.
 *
 */
 *
 @property (notatomic, assign) double adManifestTimeout; 
```

U kunt addManifestTimeout instellen door PTAdMetadata::addManifestTimeout in te stellen bij het instellen van uw advertentiemetagegevens.


```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adManifestTimeout = 5 seconds
```

Hierna volgt u de rubriek: [Metagegevens van primetime en server](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).
