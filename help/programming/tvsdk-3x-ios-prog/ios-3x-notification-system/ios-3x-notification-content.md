---
description: PTNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.
title: Inhoud voor meldingen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Meldingen voor spelerstatus, activiteit, fouten en registratie {#notifications-player-status-activity-errors-logging}

`PTNotification` objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.

Uw toepassing kan de melding- en statusgegevens ophalen. U kunt ook een registratiesysteem voor diagnostiek en validatie maken met behulp van de meldingsgegevens.

>[!NOTE]
>
>TVSDK gebruikt *`notification`* ook om te verwijzen naar `NSNotifications` ( `PTMediaPlayer` meldingen) *`event`* meldingen die worden verzonden om informatie over speleractiviteit te verstrekken.

TVSDK geeft `PTMediaPlayerNewNotificationItemEntryNotification` ook uit wanneer `PTNotification` wordt uitgegeven.

U implementeert gebeurtenislisteners om gebeurtenissen vast te leggen en erop te reageren. Veel gebeurtenissen bieden statusmeldingen `PTNotification`.

## Inhoud {#notification-content}

`PTNotification` geeft informatie over de status van de speler.

TVSDK bevat een chronologische lijst met `PTNotification`-meldingen. Elke melding bevat de volgende informatie:

* Tijdstempel
* Diagnostische metagegevens die bestaan uit de volgende elementen:

   * `type`: INFORMATIE, WAARSCHUWING of FOUT.
   * `code`: Een numerieke weergave van de kennisgeving.
   * `name`: Een door mensen leesbare beschrijving van de melding, zoals SEEK_ERROR
   * `metadata`: Sleutel-waardeparen die relevante informatie over de kennisgeving bevatten. Een sleutel met de naam `URL` levert bijvoorbeeld een waarde die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een ander  `PTNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.

## Instellen van melding {#notification-setup}

TVSDK stelt de speler in voor basismeldingen, maar u moet dezelfde instelling voor uw aangepaste meldingen uitvoeren.

Er zijn twee implementaties voor `PTNotification`:

* Om te luisteren
* Aangepaste meldingen toevoegen aan `PTNotificationHistory`

Als u naar meldingen wilt luisteren, instantieert TVSDK de klasse `PTNotification` en koppelt u deze aan een instantie van `PTMediaPlayerItem`, die aan een instantie PTMediaPlayer is gekoppeld. Er is slechts één `PTNotificationHistory` instantie per `PTMediaPlayer`.

>[!IMPORTANT]
>
>Als u aanpassingen toevoegt, moeten uw toepassingen en niet TVSDK die stappen uitvoeren.

## {#listen-to-notifications} luisteren naar meldingen

Er zijn twee manieren om naar het `PTNotification` bericht in `PTMediaPlayer` te luisteren:

1. Controleer handmatig `PTNotificationHistory` van `PTMediaPlayerItem` met een timer en controleer de verschillen:

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Gebruik de geposte [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) van `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Registreer aan `NSNotification` door de instantie van `PTMediaPlayer` te gebruiken waarvan u berichten wilt krijgen:

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Meldingscallbacks {#implement-notification-callbacks} uitvoeren

U kunt berichtcallbacks uitvoeren.

Voer de meldingscallback uit door `PTNotification` van `NSNotification` gebruikersinformatie te krijgen en zijn waarden te lezen door `PTMediaPlayerNotificationKey` te gebruiken:

```
- (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
    PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
    NSLog(@"Notification: %@", notification); 
}
```

## Aangepaste meldingen toevoegen {#add-custom-notifications}

Een aangepaste melding toevoegen:
Maak een nieuwe `PTNotification` en voeg deze toe aan de `PTNotificationHistory` met de huidige `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
