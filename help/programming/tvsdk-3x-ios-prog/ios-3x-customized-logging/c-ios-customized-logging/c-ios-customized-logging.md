---
description: U kunt uw eigen registratiesysteem implementeren.
seo-description: U kunt uw eigen registratiesysteem implementeren.
seo-title: Aangepaste logboekregistratie
title: Aangepaste logboekregistratie
uuid: f056d7d7-ec3a-4cf1-997f-72a89bbc9447
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Aangepaste logboekregistratie {#customized-logging}

U kunt uw eigen registratiesysteem implementeren.

Naast het registreren door vooraf bepaalde berichten te gebruiken, kunt u een registrerensysteem uitvoeren dat uw logboekberichten en berichten gebruikt die door TVSDK worden geproduceerd. Voor meer informatie over vooraf bepaalde berichten, zie [The Notification System](https://help.adobe.com/en_US/primetime/psdk/ios/index.html#PSDKs-concept-The_Notification_System). U kunt deze logboeken gebruiken om problemen op te lossen uw spelertoepassingen en om beter inzicht in het playback en reclamewerkschema te verstrekken.

Het aangepaste registreren gebruikt een gedeelde singletoninstantie van `PSDKPTLogFactory`, die een mechanisme verstrekt om berichten aan veelvoudige loggers te registreren. U bepaalt en voegt (registreert) één of meerdere loggers aan `PTLogFactory` toe. Dit staat u toe om veelvoudige registreerapparaten met douaneimplementaties, zoals een consoleregistreerapparaat, een Weblogger, of een registreerapparaat van de consolegeschiedenis te bepalen.

TVSDK genereert logberichten voor veel van zijn activiteiten, die de `PTLogFactory` doorstuurt naar alle geregistreerde loggers. Uw toepassing kan ook aangepaste logberichten genereren. Deze worden doorgestuurd naar alle geregistreerde loggers. Elk logger kan de berichten filteren en de juiste actie ondernemen.

Er zijn twee implementaties voor `PTLogFactory`:

* Voor het luisteren naar logboeken.
* Voor het toevoegen van logboeken aan `PTLogFactory`.

## Logbestanden {#listen-to-logs} beluisteren

Registreren voor luisteren naar logbestanden:
1. Een aangepaste klasse implementeren die volgt op het protocol `PTLogger`:

   ```
   @implementation PTConsoleLogger 
   
   + (PTConsoleLogger *) consoleLogger { 
       return [[[PTConsoleLogger alloc] init] autorelease]; 
   } 
   
   - (void)logEntry:(PTLogEntry *)entry { 
       //Log the message to the console using NSLog  
       NSLog(@"[%@] %@", entry.tag, entry.message); 
   } 
   
   @end
   ```

1. Voeg een instantie van `PTLogger` toe aan `PTLoggerFactory` om de instantie te registreren voor het ontvangen van loginggegevens:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

Hier is een voorbeeld van het filtreren logboeken door het `PTLogEntry` type te gebruiken:

```
@implementation PTConsoleLogger 
 
+ (PTConsoleLogger *) consoleLogger { 
    return [[[PTConsoleLogger alloc] init] autorelease]; 
} 
 
- (id) init { 
    self = [super init]; 
 
    if (self) { 
        self.logLevel = PTLogEntryTypeInfo; 
    } 
 
    return self; 
} 
 
- (void)logEntry:(PTLogEntry *) entry { 
    //Filtering the entry by log level  
    if (entry.type < _logLevel) { 
        return; 
    } 
 
    //Log the message to the console using NSLog NSLog(@"[%@] %@", entry.tag, entry.message); 
} 
 
@end
```

## Nieuwe logberichten toevoegen {#add-new-log-messages}

Registreren om naar logbestanden te luisteren:

Maak een nieuwe `PTLogEntry` en voeg deze toe aan `thePTLogFactory`:

U kunt een `PTLogEntry` manueel concretiseren en het toevoegen aan `PTLogFactory` gedeelde instantie of één van de macro&#39;s gebruiken om de zelfde taak te verwezenlijken.

Hier volgt een voorbeeld van het registreren met de macro `PTLogDebug`:

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
