---
description: U kunt meerdere inhoudsoplossers gebruiken om verschillende tijdlijnbewerkingen af te handelen.
seo-description: U kunt meerdere inhoudsoplossers gebruiken om verschillende tijdlijnbewerkingen af te handelen.
seo-title: Inhoud-oplossers voor verwijderen/vervangen
title: Inhoud-oplossers voor verwijderen/vervangen
uuid: d43d54be-e04a-49dd-a695-e4e8f981ccb4
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Inhoud-oplossers voor verwijderen/vervangen {#content-resolvers-for-ad-deletion-replacement}

U kunt meerdere inhoudsoplossers gebruiken om verschillende tijdlijnbewerkingen af te handelen.

```java
public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { 
    List<ContentResolver> resolvers = new ArrayList<ContentResolver>(); 
    MediaPlayerItemConfig itemConfig = item.getConfig(); 
    if(itemConfig) { 
        CustomRangeMetadata customRanges = itemConfig.getCustomRangeMetadata(); 
        if (customRanges) { 
            List<ReplaceTimeRange> timeRanges = customRanges.getTimeRangeList(); 
 
            if (timeRanges && timeRanges.size() > 0) { 
                //CustomRangeResolver is activated by the presence of CustomRanges 
                resolvers.add(new CustomRangeResolver()); 
            } 
        } 
        AdvertisingMetadata metadata = itemConfig.getAdvertisingMetadata(); 
        if (metadata) { 
            if (metadata instanceOf AuditudeSettings)  
            resolvers.add(new AuditudeResolver(getContext());                                      
        } 
    } 
    //Add your custom resolver if any 
    resolvers.add(MyOpportunityGenerator(item)); 
    return resolvers; 
} 
```
