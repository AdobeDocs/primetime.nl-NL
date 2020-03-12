---
description: U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.
seo-description: U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.
seo-title: Metagegevens met tijdslimiet gebruiken
title: Metagegevens met tijdslimiet gebruiken
uuid: 9bbdaefa-4ac5-4e08-92b4-15ebe5c46864
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b

---


# Metagegevens met tijdslimiet gebruiken{#use-timed-metadata}

U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.

Als u deze opgeslagen `PTTimedMetadata` objecten tijdens het afspelen wilt gebruiken, gebruikt u het opgeslagen woordenboek van [Opgeslagen metagegevensobjecten opslaan terwijl ze worden verzonden](../../../tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-timed-metadata-store.md).

1. Extraheer en werk de huidige afspeeltijd van dit bericht bij en zoek alle `PTTimedMetadata` objecten met begintijden die overeenkomen met de huidige afspeeltijd.

   U kunt deze objecten gebruiken om verschillende handelingen uit te voeren.

   Bijvoorbeeld:

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification 
   { 
       CMTimeRange seekableRange = self.player.seekableRange; 
       if (CMTIMERANGE_IS_VALID(seekableRange)) 
       { 
           int currentTime = (int) CMTimeGetSeconds(self.player.currentTime); 
           NSArray *allKeys = timedMetadataCollection ? [timedMetadataCollection allKeys] : [NSArray array]; 
           NSMutableArray *timedMetadatasToDelete = [[[NSMutableArray alloc] init] autorelease]; 
           int count = [allKeys count]; 
   
           for (int i=count - 1; i > -1; i--) 
           { 
              NSNumber *currTimedMetadataTime = allKeys[i]; 
              if ([currTimedMetadataTime integerValue] == currentTime) 
              { 
               /* 
                   Use the timed metadata here and remove it from the collection. 
               */ 
                NSLog (@"IN PLAYBACK TIME %i TO EXECUTE TIMEDMETADATA %@ scheduled at time %f",currentTime,currTimedMetadata.name,CMTimeGetSeconds(currTimedMetadata.time)); 
   
               PTTimedMetadata *currTimedMetadata = [timedMetadataCollection objectForKey:currTimedMetadataTime]; 
               [timedMetadatasToDelete addObject:currTimedMetadataTime]; 
              } 
           } 
   
           for (int i=0; i<[timedMetadatasToDelete count]; i++) 
           { 
               NSNumber *timedMetadataToDelete = timedMetadatasToDelete[i]; 
               [timedMetadataCollection removeObjectForKey:timedMetadataToDelete]; 
           } 
       } 
   }
   ```

1. Verwijder stijlexemplaren regelmatig uit de lijst om te voorkomen dat het geheugen voortdurend toeneemt. `PTTimedMetadata`
