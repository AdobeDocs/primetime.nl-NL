---
description: U kunt uw eigen registratiesysteem implementeren.
title: Aangepaste logboekregistratie
exl-id: 8b6a916e-783e-40e1-8a3d-706b57a6ff63
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Aangepaste logboekregistratie {#customized-logging}

U kunt uw eigen registratiesysteem implementeren.

Naast het registreren door vooraf bepaalde berichten te gebruiken, kunt u een registrerensysteem uitvoeren dat uw logboekberichten en berichten gebruikt die door TVSDK worden geproduceerd. Voor meer informatie over vooraf gedefinieerde meldingen raadpleegt u [Het meldingssysteem](https://help.adobe.com/en_US/primetime/psdk/ios/index.html#PSDKs-concept-The_Notification_System). U kunt deze logboeken gebruiken om problemen op te lossen uw spelertoepassingen en om beter inzicht in het playback en reclamewerkschema te verstrekken.

Het aangepaste registreren gebruikt een gedeelde singleton instantie van `PSDKPTLogFactory`, die een mechanisme verstrekt om berichten aan veelvoudige registreerapparaten te registreren. U definieert een of meer loggers en voegt deze toe aan de `PTLogFactory`. Dit staat u toe om veelvoudige registreerapparaten met douaneimplementaties, zoals een consoleregistreerapparaat, een Weblogger, of een registreerapparaat van de consolegeschiedenis te bepalen.

TVSDK genereert logberichten voor veel van zijn activiteiten, die de `PTLogFactory` doorsturen naar alle geregistreerde loggers. Uw toepassing kan ook aangepaste logberichten genereren. Deze worden doorgestuurd naar alle geregistreerde loggers. Elk logger kan de berichten filteren en de juiste actie ondernemen.

Er zijn twee implementaties voor `PTLogFactory`:

* Voor het luisteren naar logboeken.
* Voor het toevoegen van logbestanden aan een `PTLogFactory`.

## Logbestanden beluisteren {#listen-to-logs}

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

1. Als u de instantie wilt registreren voor het ontvangen van loginggegevens, voegt u een instantie van de optie `PTLogger` aan de `PTLoggerFactory`:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

Hier is een voorbeeld van het filtreren logboeken door te gebruiken `PTLogEntry` type:

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

Een nieuwe `PTLogEntry` en voeg deze toe aan `thePTLogFactory`:

U kunt handmatig een `PTLogEntry` en voeg het toe aan `PTLogFactory` gedeelde instantie of gebruik een van de macro&#39;s om dezelfde taak uit te voeren.

Hier is een voorbeeld van het registreren gebruikend `PTLogDebug` macro:

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
