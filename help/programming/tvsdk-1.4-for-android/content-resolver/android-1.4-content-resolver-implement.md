---
description: U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.
title: Een aangepaste contentoplosser implementeren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Een aangepaste contentoplosser implementeren {#implement-a-custom-content-resolver}

U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.

Wanneer TVSDK een nieuwe kans detecteert, doorloopt het de geregistreerde contentoplossers die naar een mogelijkheid zoeken die deze mogelijkheid kan oplossen. De eerste die waar terugkeert wordt geselecteerd voor het oplossen van de kans. Als er geen inhoudoplosser kan worden gemaakt, wordt die mogelijkheid overgeslagen. Omdat het proces voor het oplossen van inhoud meestal asynchroon is, is de oplosser van de inhoud verantwoordelijk voor het op de hoogte brengen wanneer het proces is voltooid.

1. Een aangepaste `AdvertisingFactory` instantie en overschrijving `createContentResolver`.

   Bijvoorbeeld:

   ```java
   new AdvertisingFactory() { 
       ... 
       @Override 
       public ContentResolver createContentResolver(MediaPlayerItem item) { 
           Metadata metadata = _mediaPlayer.getCurrentItem().getResource().getMetadata(); 
           if (metadata != null) { 
               if (metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue())) { 
                   return new AuditudeResolver(getActivity().getApplicationContext()); 
               } else if (metadata.containsKey(DefaultMetadataKeys.JSON_METADATA_KEY.getValue())) { 
                   return new MetadataResolver(); 
               } else if (metadata.containsKey(DefaultMetadataKeys.TIME_RANGES_METADATA_KEY.getValue())) { 
                   return new CustomAdMarkersContentResolver(); 
               } else if (metadata.containsKey(CustomAdResolver.CUSTOM_METADATA_KEY)) { 
                   return new CustomAdResolver(); 
               } 
           } 
           return null; 
       } 
       ... 
   }
   ```

1. De advertentiecliënt registreren bij `MediaPlayer`.

   Bijvoorbeeld:

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. Een `AdvertisingMetadata` als volgt naar TVSDK te verwijzen:
   1. Een `AdvertisingMetadata` object en `MetadataNode` object.
   1. Sla de `AdvertisingMetadata` object naar `MetadataNode`.

   ```java
   MetadataNode result = new MetadataNode(); 
   result.setNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue(),  
                  advertisingMetadata);
   ```

1. Een aangepaste ad resolver-klasse maken die de klasse `ContentResolver` klasse.
   1. Overschrijf deze beveiligde functie in de aangepaste en oplosser:

      ```java
      void doResolveAds(Metadata metadata,  
                        PlacementOpportunity placementOpportunity)
      ```

      Metagegevens bevatten uw `AdvertisingMetada`. Gebruik deze voor het volgende `TimelineOperation` vectorgeneratie.

   1. Voor elke plaatsingskans maakt u een `Vector<TimelineOperation>`.

      De vector kan leeg zijn, maar niet null.

      Dit voorbeeld `TimelineOperation` biedt een structuur voor `AdBreakPlacement`:

      ```java
      AdBreakPlacement(AdBreak.createAdBreak( 
                                ads,       // Vector<Ad> 
                                time,      // Ad Break start time. Note: local time on the timeline 
                                duration,  // Ad Break duration 
                                tag()      // An arbitrary string value that can be attached to  
                                           // the AdBreak object. 
                               ), placementInformation  // Retrieved from PlacementOpportunity 
      )
      ```

   1. Nadat de advertenties zijn opgelost, roep één van de volgende functies:

      * Als de advertentie succesvol is: `notifyResolveComplete(Vector<TimelineOperation> proposals)`
      * Als de advertentie-oplossing mislukt: `notifyResolveError(Error error)`

      Als dit bijvoorbeeld mislukt:

      ```java
      Metadata metadata = new MetadataNode(); 
      metadata.setValue("NATIVE_ERROR_CODE", exception.getCause().toString()); 
      error.setMetadata(metadata);
      ```

<!--<a id="example_4F0D7692A92E480A835D6FDBEDBE75E7"></a>-->

Deze aangepaste voorbeeldbewerker doet een HTTP-aanvraag aan de advertentieserver en ontvangt een JSON-reactie.

```java
public class CustomAdResolver extends ContentResolver { 
    ... 
    @Override 
    protected void doResolveAds(Metadata metadata, PlacementOpportunity placementOpportunity) { 
        ... 
        if (resolveSuccess == true) { 
            notifyResolveComplete(Vector<TimelineOperation> proposals); 
        } 
        else { 
            notifyResolveError(Error error); 
        } 
    } 
    ... 
}
```

Voorbeeld van JSON-serverreactie voor een live stream:

```
{     
    "response": { 
        "breaks": [ { 
            "start": 0, 
            "ads": [ { 
                "id": 1001, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/geico/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset1", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } 
        ] }, 
        { 
            "start": -1, 
            "ads": [ { 
                "id": 1003, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/priceline/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset3", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        } ] 
    } 
} 
```

Voorbeeld van JSON en serverreactie voor VOD:

```
{     
    "response": { 
        "breaks": [ { 
            "start": 0, 
            "ads": [ { 
                "id": 1001, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/geico/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset1", 
                    "resource_type": "" 
                }, 
                "companion_assets": {  
                } 
            }, 
            { 
                "id": 1002, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/crescent/playlist.m3u8", 
                    "duration": 15000, 
                    "id": "asset2", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        }, 
        { 
            "start": 50000, 
            "ads": [ { 
                "id": 1003, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/priceline/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset3", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        }, 
        { 
            "start": 100000000, 
            "ads": [ { 
                "id": 1004, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/camry/playlist.m3u8", 
                    "duration": 15000, 
                    "id": "asset4", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        } ] 
    } 
} 
```
