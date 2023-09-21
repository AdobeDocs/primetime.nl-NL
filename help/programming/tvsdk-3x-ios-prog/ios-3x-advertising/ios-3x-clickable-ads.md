---
description: TVSDK biedt u informatie zodat u op doorklikadvertenties kunt werken. Terwijl u de interface van de speler maakt, moet u bepalen hoe u moet reageren wanneer een gebruiker op een klikbare advertentie klikt.
title: Klikbare advertenties
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Klikbare advertenties {#clickable-ads}

TVSDK biedt u informatie zodat u op doorklikadvertenties kunt werken. Terwijl u de interface van de speler maakt, moet u bepalen hoe u moet reageren wanneer een gebruiker op een klikbare advertentie klikt.

In TVSDK voor iOS kan alleen op lineaire advertenties worden geklikt.

## Reageren op klikken op advertenties {#section_537AF2593FDB4257B81AAE2103B0C719}

Wanneer een gebruiker op een advertentie, een banneradvertentie of een verwante knop klikt, moet uw toepassing reageren. TVSDK biedt u informatie over de doel-URL voor de klik.

1. Als u een gebeurtenislistener voor TVSDK wilt instellen en de doorklikinformatie wilt weergeven, voegt u een waarnemer voor `PTMediaPlayerAdClickNotification`.

   >[!NOTE]
   >
   >Wanneer een gebruiker op een advertentie, een banneradvertentie of een verwante knop klikt, verzendt TVSDK dit bericht, inclusief informatie over de bestemming voor de klik.

1. Gebruikersinteracties controleren op klikbare advertenties.
1. Wanneer de gebruiker de advertentie of knop aanraakt of erop klikt, gebruikt u `[_player notifyClick:_currentAd.primaryAsset];`.
1. Luister naar de `PTMediaPlayerAdClickNotification` gebeurtenis van TVSDK.
1. Als u de doorklikURL en verwante informatie wilt ophalen, gebruikt u de `PTMediaPlayerAdClickURLKey` object.
1. De video pauzeren.
1. Gebruik de doorklikinformatie om de advertentie-door URL en de verwante informatie te tonen.

   >[!NOTE]
   >
   >U kunt de informatie bijvoorbeeld op een van de volgende manieren weergeven:

   * In uw toepassing door klik-door URL in browser te openen.

     Op bureaubladplatforms worden de video en het afspeelgebied gebruikt om doorklikURL&#39;s aan te roepen wanneer de gebruiker klikt.
   * Gebruikers omleiden naar hun externe mobiele webbrowser.

     Op mobiele apparaten worden de video en het afspeelgebied gebruikt voor andere functies, zoals het verbergen en weergeven van besturingselementen, het pauzeren van het afspelen, het uitbreiden naar het volledige scherm, enzovoort. Op deze apparaten wordt een aparte weergave, zoals een sponsor, gebruikt om de URL voor klikken te starten.

1. Sluit het browservenster waarin de doorklikinformatie wordt weergegeven en hervat het afspelen van de video.

   Bijvoorbeeld:

   ```
      // Listening for click notification  
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdClick:)  
    name:PTMediaPlayerAdClickNotification object:self.player]; 
   - (void) onMediaPlayerAdClick:(NSNotification *) notification { 
      NSString *url = [notification.userInfo objectForKey:PTMediaPlayerAdClickURLKey];  
      if (url != nil) { 
          [self openBrowser:[NSURL URLWithString:url]]; 
      } 
   } 
   ```
