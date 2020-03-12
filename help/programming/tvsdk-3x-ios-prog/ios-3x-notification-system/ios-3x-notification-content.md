---
description: PTNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.
seo-description: PTNotification-objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.
seo-title: Inhoud voor meldingen
title: Inhoud voor meldingen
uuid: d42d2e89-1bdd-4be0-8a69-821fec6bbc75
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Meldingen voor spelerstatus, activiteit, fouten en logboekregistratie {#notifications-player-status-activity-errors-logging}

`PTNotification` objecten bieden informatie over wijzigingen in spelerstatus, waarschuwingen en fouten. Fouten die het afspelen van de video stoppen, leiden ook tot een wijziging in de status van de speler.

Uw toepassing kan de melding- en statusgegevens ophalen. U kunt ook een registratiesysteem voor diagnostiek en validatie maken met behulp van de meldingsgegevens.

>[!NOTE]
>
>TVSDK gebruikt ook *`notification`* om te verwijzen naar `NSNotifications` ( `PTMediaPlayer` ) *`event`* -meldingen die worden verzonden voor informatie over speleractiviteiten.

TVSDK geeft ook problemen `PTMediaPlayerNewNotificationItemEntryNotification` als het probleem zich voordoet `PTNotification`.

U implementeert gebeurtenislisteners om gebeurtenissen vast te leggen en erop te reageren. Veel gebeurtenissen bieden `PTNotification` statusmeldingen.

## Inhoud voor meldingen {#notification-content}

`PTNotification` geeft informatie over de status van de speler.

TVSDK verstrekt een chronologische lijst van `PTNotification` berichten. Elke melding bevat de volgende informatie:

* Tijdstempel
* Diagnostische metagegevens die bestaan uit de volgende elementen:

   * `type`: INFORMATIE, WAARSCHUWING of FOUT.
   * `code`: Een numerieke weergave van de kennisgeving.
   * `name`: Een door mensen leesbare beschrijving van de melding, zoals SEEK_ERROR
   * `metadata`: Sleutel-waardeparen die relevante informatie over de kennisgeving bevatten. Een benoemde sleutel `URL` biedt bijvoorbeeld een waarde die een URL is die gerelateerd is aan het bericht.

   * `innerNotification`: Een verwijzing naar een ander `PTNotification` object dat rechtstreeks van invloed is op deze melding.

U kunt deze informatie lokaal opslaan voor latere analyse of naar een externe server verzenden voor registratie en grafische weergave.

## Meldingsinstelling {#notification-setup}

TVSDK stelt de speler in voor basismeldingen, maar u moet dezelfde instelling voor uw aangepaste meldingen uitvoeren.

Er zijn twee implementaties voor `PTNotification`:

* Om te luisteren
* Aangepaste meldingen toevoegen aan `PTNotificationHistory`

Om naar meldingen te luisteren, instantieert TVSDK de `PTNotification` klasse en koppelt deze aan een instantie van de `PTMediaPlayerItem`klasse, die aan een instantie PTMediaPlayer is gekoppeld. Er is slechts één `PTNotificationHistory` instantie per `PTMediaPlayer`.

>[!IMPORTANT]
>
>Als u aanpassingen toevoegt, moeten uw toepassingen en niet TVSDK die stappen uitvoeren.

## Meldingen beluisteren {#listen-to-notifications}

Er zijn twee manieren om naar het `PTNotification` bericht in te luisteren `PTMediaPlayer`:

1. Controleer handmatig het `PTNotificationHistory` van de timer `PTMediaPlayerItem` met een timer en controleer de verschillen:

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. Gebruik de geposte [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) van `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. Registreer u bij de `NSNotification` gebruiker met behulp van het exemplaar van het `PTMediaPlayer` formulier waarvan u meldingen wilt ontvangen:

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## Meldingscallbacks implementeren {#implement-notification-callbacks}

U kunt berichtcallbacks uitvoeren.

Voer bericht callback uit door het `PTNotification` van de `NSNotification` gebruikersinformatie te krijgen en zijn waarden te lezen door te gebruiken `PTMediaPlayerNotificationKey`:

```
- (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
    PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
    NSLog(@"Notification: %@", notification); 
}
```

## Aangepaste meldingen toevoegen {#add-custom-notifications}

Een aangepaste melding toevoegen:
Maak een nieuw bestand `PTNotification` en voeg het toe aan het `PTNotificationHistory` huidige bestand `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
