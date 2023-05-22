---
description: Voer de juiste berichtlistener(s) uit om meldingen over codes in het manifest te ontvangen.
title: Listeners toevoegen voor meldingen van getimede metagegevens
exl-id: 30606188-ee0e-419d-96af-3571c8836422
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Listeners toevoegen voor meldingen van getimede metagegevens {#add-listeners-for-timed-metadata-notifications}

Voer de juiste berichtlistener(s) uit om meldingen over codes in het manifest te ontvangen.

U kunt getimede metagegevens controleren door te luisteren naar de volgende gebeurtenissen, die uw toepassing op de hoogte stellen van verwante activiteiten:

* `PTTimedMetadataChangedNotification`: Telkens wanneer een unieke geabonneerde tag wordt geïdentificeerd tijdens het parseren van de inhoud, bereidt TVSDK een nieuwe tag voor `PTTimedMetadata` en verzendt deze melding.

   Het object bevat de naam van de tag waarop u zich hebt geabonneerd, de lokale tijd tijdens het afspelen waar deze tag wordt weergegeven en andere gegevens.

* `PTMediaPlayerTimeChangeNotification` : Voor live/lineaire streams waarbij het manifest/de afspeellijst periodiek wordt vernieuwd, kunnen extra aangepaste tags worden weergegeven in de bijgewerkte afspeellijst/het bijgewerkte manifest, zodat aanvullende `TimedMetadata` objecten kunnen worden toegevoegd aan de `MediaPlayerItem.timedMetadata` eigenschap.

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

   * Toegang krijgen tot `timedMetadataCollection` eigenschap van `PTMediaPlayerItem`, die bestaat uit alle `PTTimedMetadata` objecten die tot dusver zijn aangemeld.
