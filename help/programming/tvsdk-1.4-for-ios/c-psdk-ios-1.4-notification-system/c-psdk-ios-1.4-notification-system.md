---
description: PTNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.
title: Meldingen voor spelerstatus, activiteit, fouten en logbestanden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Meldingen voor spelerstatus, activiteit, fouten en logboekregistratie  {#notifications-for-player-status-activity-errors-and-logs-overview}

PTNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.

Uw toepassing kan de melding- en statusgegevens ophalen. U kunt ook een registratiesysteem voor diagnostiek en validatie maken met behulp van de meldingsgegevens.

>[!IMPORTANT]
>
>TVSDK gebruikt ook *`notification`* verwijzen naar `NSNotifications` ( `PTMediaPlayer` meldingen) *`event`* meldingen die worden verzonden voor informatie over speleractiviteiten.

TVSDK heeft ook problemen `PTMediaPlayerNewNotificationItemEntryNotification` wanneer `PTNotification`.

U implementeert gebeurtenislisteners om gebeurtenissen vast te leggen en erop te reageren. Veel gebeurtenissen bieden `PTNotification` statusmeldingen.

## Inhoud voor meldingen {#notification-content}

PTNotification biedt informatie die gerelateerd is aan de status van de speler.

TVSDK verstrekt een chronologische lijst van `PTNotification` meldingen. Elke melding bevat de volgende informatie:

* Tijdstempel
* Diagnostische metagegevens die bestaan uit de volgende elementen:

   * `type`: INFO, WARN of ERROR.
   * `code`: Een numerieke weergave van de kennisgeving.
   * `name`: Een door mensen leesbare beschrijving van de melding, zoals SEEK_ERROR
   * `metadata`: sleutel/waardeparen die relevante informatie over de kennisgeving bevatten. Bijvoorbeeld een toets met de naam `URL` Hiermee wordt een waarde opgegeven die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een andere `PTNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.

## Meldingsinstelling {#notification-setup}

TVSDK stelt de speler in voor basismeldingen, maar u moet dezelfde instelling voor uw aangepaste meldingen uitvoeren.

Er zijn twee implementaties voor `PTNotification`:

* Om te luisteren
* Aangepaste meldingen toevoegen aan `PTNotificationHistory`

Om meldingen te beluisteren, instantieert TVSDK de `PTNotification` en koppelt deze aan een instantie van de klasse `PTMediaPlayerItem`, die aan een instantie PTMediaPlayer wordt vastgemaakt. Er is slechts één `PTNotificationHistory` instantie per `PTMediaPlayer`.

>[!IMPORTANT]
>
>Als u aanpassingen toevoegt, moeten uw toepassingen en niet TVSDK die stappen uitvoeren.

## Luisteren naar meldingen {#listen-to-notifications}

Er zijn twee manieren om naar de `PTNotification` in de `PTMediaPlayer`:

1. Handmatig de optie `PTNotificationHistory` van de `PTMediaPlayerItem` met een timer en controleer de verschillen:

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. De gepost gebruiken [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) van de `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Registreren bij de `NSNotification` door de instantie van de `PTMediaPlayer` waarvan u meldingen wilt ontvangen:

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Meldingscallbacks implementeren {#implement-notification-callbacks}

U kunt berichtcallbacks uitvoeren.

1. Implementeer de meldingscallback door de `PTNotification` van de `NSNotification` gebruikersinformatie en het lezen van zijn waarden door te gebruiken `PTMediaPlayerNotificationKey`:

   ```
   - (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
       PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
       NSLog(@"Notification: %@", notification); 
   }
   ```

## Aangepaste meldingen toevoegen {#add-custom-notifications}

Een aangepast bericht toevoegen: een nieuw bericht maken `PTNotification` en voeg het toe aan `PTNotificationHistory` door de huidige `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
