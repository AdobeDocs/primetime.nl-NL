---
description: U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.
seo-description: U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.
seo-title: Een aangepaste contentoplosser implementeren
title: Een aangepaste contentoplosser implementeren
uuid: bc0eda17-9b5d-4733-8e93-790758e68df5
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Een aangepaste contentoplosser implementeren {#implement-a-custom-content-resolver}

U kunt uw eigen inhoudsoplossers implementeren op basis van de standaardoplossers.

Wanneer TVSDK een nieuwe kans genereert, doorloopt het de geregistreerde contentoplossers die naar een mogelijkheid zoeken die die kans kan oplossen. De eerste die terugkeert `true` wordt geselecteerd om de kans op te lossen. Als er geen oplossing voor inhoud mogelijk is, wordt die mogelijkheid overgeslagen. Omdat het proces voor het oplossen van inhoud meestal asynchroon is, brengt de contentoplosser TVSDK op de hoogte wanneer het proces is voltooid.

1. Voer uw eigen douane uit `ContentFactory`, door de `ContentFactory` interface uit te breiden en met voeten te treden `retrieveResolvers`.

   Bijvoorbeeld:

   ```java
   class MyContentFactory extends ContentFactory { 
       @Override 
       public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { 
           List<ContentResolver> resolvers = new ArrayList<ContentResolver>(); 
           MediaPlayerItemConfig itemConfig = item.getConfig(); 
           if(itemConfig) { 
               CustomRangeMetadata customRanges = itemConfig.getCustomRangeMetadata(); 
               if (customRanges) { 
                   List<ReplaceTimeRange> timeRanges = customRanges.getTimeRangeList(); 
   
                   if (timeRanges && timeRanges.size() > 0) 
                   { 
                   // CustomRangeResolver is only activated by the presence of CustomRanges in configuration 
                   resolvers.add(new CustomRangeResolver()); 
                   } 
               } 
               AdvertisingMetadata metadata = itemConfig.getAdvertisingMetadata(); 
               if (metadata) { 
                   if (metadata instanceOf AuditudeSettings)  
                       resolvers.add(new AuditudeResolver(getContext());    
                   } 
               } 
           // add your custom resolver if any 
           resolvers.add(MyOpportunityGenerator(item)); 
           return resolvers; 
       } 
       ... 
   } 
   ```

1. Registreer de `ContentFactory` gegevens bij de `MediaPlayer`.

   Bijvoorbeeld:

   ```java
   //Register the custom content factory with the media player 
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new MyContentFactory()); 
   
   //Pass this config while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config); 
   
   // OR use MediaPlayerItemLoader to pre-load a resource 
   id = 23; 
   itemLoader.load(resource, id, config);
   ```

1. Geef een `AdvertisingMetadata` object als volgt door aan TVSDK:
   1. Maak een `AdvertisingMetadata` object.
   1. Sla het `AdvertisingMetadata` object op in `MediaPlayerItemConfig`.

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. Maak een aangepaste ad resolver-klasse die de `ContentResolver` klasse uitbreidt.
   1. Overschrijf in de aangepaste en oplosser `doConfigure`, `doCanResolve`, `doResolve`, `doCleanup`:

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      Je krijgt je `advertisingMetadata` van het object dat is doorgegeven `doConfigure`:

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. Maak voor elke plaatsingskans een `List<TimelineOperation>`.

      Dit voorbeeld `TimelineOperation` biedt een structuur voor `AdBreakPlacement`:

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. Nadat de advertenties zijn opgelost, roep één van de volgende functies:

      * Als de advertentie slaagt, roep `process(List<TimelineOperation> proposals)` en `notifyCompleted(Opportunity opportunity)` op `ContentResolverClient`

         ```java
         _client.process(timelineOperations); 
         _client.notifyCompleted(opportunity); 
         ```

      * Als de advertentie-oplossing mislukt, roept u `notifyResolveError` de `ContentResolverClient`

         ```java
         _client.notifyFailed(Opportunity opportunity, PSDKErrorCode error);
         ```

         Bijvoorbeeld:

         ```java
         _client.notifyFailed(opportunity, UNSUPPORTED_OPERATION);
         ```

<!--<a id="example_463B718749504A978F0B887786844C39"></a>-->

Deze voorbeeldaangepaste en oplosser verhelpt een mogelijkheid en biedt een eenvoudige advertentie:

```java
public class CustomContentResolver extends ContentResolver { 
    protected void doConfigure(MediaPlayerItem item){} 
 
    protected boolean doCanResolve(Opportunity opportunity) {  
        return true;  
    } 
 
    protected void doResolve(Opportunity opportunity) { 
        _client.process(createAdBreakPlacementsFor(opportunity.getPlacement())); 
        _client.notifyCompleted(opportunity); 
    } 
 
    private List<TimelineOperation> createAdBreakPlacementsFor(Placement placementInformation) { 
        List<Ad> ads = new ArrayList<Ad>(); 
        AdAsset adAsset = new AdAsset("101", 15000, new MediaResource( 
          "https: . . ..m3u8", MediaResource.Type.HLS, null), null, null); 
 
        Ad ad = Ad.linearFromAsset("101", adAsset, null, null, false); 
        ads.add(ad); 
        AdBreak adBreak = new AdBreak(ads, null, AdInsertionType.CLIENT_INSERTED); 
 
        List<TimelineOperation> result = new ArrayList<TimelineOperation>(); 
 
        result.add(new AdBreakPlacement(placementInformation, adBreak)); 
        return result; 
    } 
 
    protected void doCleanup() {} 
} 
```

