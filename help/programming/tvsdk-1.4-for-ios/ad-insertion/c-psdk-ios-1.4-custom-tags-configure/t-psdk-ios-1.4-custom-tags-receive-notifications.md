---
description: Voer de juiste berichtlistener(s) uit om meldingen over codes in het manifest te ontvangen.
title: Listeners toevoegen voor meldingen van getimede metagegevens
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Listeners toevoegen voor meldingen van getimede metagegevens {#add-listeners-for-timed-metadata-notifications}

Voer de juiste berichtlistener(s) uit om meldingen over codes in het manifest te ontvangen.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `PTTimedMetadataChangedNotification`: Telkens wanneer een unieke geabonneerde tag wordt geïdentificeerd tijdens het parseren van de inhoud, bereidt TVSDK een nieuwe tag voor `PTTimedMetadata` en verzendt deze melding.

  Het object bevat de naam van de tag waarop u zich hebt geabonneerd, de lokale tijd tijdens het afspelen waar deze tag wordt weergegeven en andere gegevens.

* `PTMediaPlayerTimeChangeNotification` : Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het bijgewerkte manifest, zodat extra `TimedMetadata` objecten kunnen worden toegevoegd aan de `MediaPlayerItem.timedMetadata` eigenschap.

  Deze gebeurtenis brengt uw toepassing op de hoogte wanneer dit gebeurt.

  U kunt de metagegevens met tijdinstellingen op een van de volgende manieren ophalen.

   * Stel de toepassing zo in dat deze zichzelf als listener toevoegt aan de `PTTimedMetadataChangedNotification` meldingen verzenden en het object ophalen met `PTTimedMetadataKey`.

     ```
     [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
       name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
     
     - (void) onTimedMetadataChanged:(NSNotification *) notification { 
         NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
         PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
     }
     ```

   * Toegang krijgen tot de `timedMetadataCollection` eigenschap van `PTMediaPlayerItem`, die bestaat uit alle `PTTimedMetadata` objecten die tot dusver zijn aangemeld.
