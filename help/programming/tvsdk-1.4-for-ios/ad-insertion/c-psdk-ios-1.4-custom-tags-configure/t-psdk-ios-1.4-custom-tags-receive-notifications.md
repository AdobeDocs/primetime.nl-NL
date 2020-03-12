---
description: Voer de juiste berichtlistener(s) uit om meldingen over codes in het manifest te ontvangen.
seo-description: Voer de juiste berichtlistener(s) uit om meldingen over codes in het manifest te ontvangen.
seo-title: Listeners toevoegen voor meldingen van getimede metagegevens
title: Listeners toevoegen voor meldingen van getimede metagegevens
uuid: dcd1bd92-0617-4eab-8b06-7301aaff42f3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Listeners toevoegen voor meldingen van getimede metagegevens {#add-listeners-for-timed-metadata-notifications}

Voer de juiste berichtlistener(s) uit om meldingen over codes in het manifest te ontvangen.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `PTTimedMetadataChangedNotification`: Telkens wanneer een unieke geabonneerde tag wordt geïdentificeerd tijdens het parseren van de inhoud, bereidt TVSDK een nieuw `PTTimedMetadata` object voor en verzendt deze melding.

   Het object bevat de naam van de tag waarop u zich hebt geabonneerd, de lokale tijd tijdens het afspelen waar deze tag wordt weergegeven en andere gegevens.

* `PTMediaPlayerTimeChangeNotification` : Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het manifest, zodat aanvullende `TimedMetadata` objecten aan de `MediaPlayerItem.timedMetadata` eigenschap kunnen worden toegevoegd.

   Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

   U kunt de metagegevens met tijdinstellingen op een van de volgende manieren ophalen.

   * Stel de toepassing zo in dat deze zichzelf als listener aan het `PTTimedMetadataChangedNotification` bericht toevoegt en het object ophaalt met behulp van `PTTimedMetadataKey`.

      ```
      [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
        name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
      
      - (void) onTimedMetadataChanged:(NSNotification *) notification { 
          NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
          PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
      }
      ```

   * Open de `timedMetadataCollection` eigenschap van `PTMediaPlayerItem`, die bestaat uit alle `PTTimedMetadata` objecten die tot nu toe zijn aangemeld.

