---
description: Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
title: Luisteren naar gebeurtenissen in Primetime Player
exl-id: 3a740245-a9e1-4e36-8761-f9f4b4e85b93
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Overzicht {#implement-event-listeners-and-callbacks-overview}

Met gebeurtenishandlers kan TVSDK reageren op gebeurtenissen. Wanneer een gebeurtenis voorkomt, roept het gebeurtenismechanisme van TVSDK uw geregistreerde gebeurtenismanager en gaat de gebeurtenisinformatie tot de manager over.

De Flash Runtime verstrekt een generisch gebeurtenismechanisme, dat TVSDK ook gebruikt en een reeks douanegebeurtenissen bepaalt. Uw toepassing moet gebeurtenislisteners implementeren voor TVSDK-gebeurtenissen die van invloed zijn op uw toepassing.

1. Bepaal voor welke gebeurtenissen uw toepassing moet luisteren.

   * **Vereiste gebeurtenissen**: Luister naar alle afspeelgebeurtenissen.

      >[!IMPORTANT]
      >
      >De afspeelgebeurtenis `MediaPlayerStatusChangeEvent.STATUS_CHANGE` geeft de spelerstatus weer, inclusief fouten. Een van de staten kan de volgende stap van de speler beïnvloeden.

   * **Andere gebeurtenissen**: Optioneel, afhankelijk van uw toepassing.

      Als u bijvoorbeeld reclame in het afspelen opneemt, luistert u naar alles `AdBreakPlaybackEvent` en `AdPlaybackEvent` gebeurtenissen.

1. Implementeer gebeurtenislisteners voor elke gebeurtenis.

   TVSDK retourneert parameterwaarden aan uw callbacks van de gebeurtenislistener. Deze waarden bieden relevante informatie over de gebeurtenis die u in de listeners kunt gebruiken om de juiste handelingen uit te voeren.

   De `Event` De klasse maakt een lijst van alle callback interfaces. Elke interface toont de parameters die voor die interface zijn teruggekeerd.

   Bijvoorbeeld:

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Registreer uw callback luisteraars met `MediaPlayer` object gebruiken `MediaPlayer.addEventListener`.

   `MediaPlayer` extends `flash.events.IEventDispatcher`, die deel uitmaakt van de kernbestanden van de Flash-speler en de functies bevat `addEventListener` en `removeEventListener`.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```
