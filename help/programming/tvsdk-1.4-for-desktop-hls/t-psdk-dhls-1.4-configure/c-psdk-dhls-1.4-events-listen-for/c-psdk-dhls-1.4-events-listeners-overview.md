---
description: Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
seo-description: Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
seo-title: Luisteren naar gebeurtenissen in Primetime Player
title: Luisteren naar gebeurtenissen in Primetime Player
uuid: e72782bf-9d26-4285-85e4-fd4d803c1bbe
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Overzicht {#implement-event-listeners-and-callbacks-overview}

Met gebeurtenishandlers kan TVSDK reageren op gebeurtenissen. Wanneer een gebeurtenis voorkomt, roept het gebeurtenismechanisme van TVSDK uw geregistreerde gebeurtenismanager en gaat de gebeurtenisinformatie tot de manager over.

De Flash Runtime verstrekt een generisch gebeurtenismechanisme, dat TVSDK ook gebruikt en een reeks douanegebeurtenissen bepaalt. Uw toepassing moet gebeurtenislisteners implementeren voor TVSDK-gebeurtenissen die van invloed zijn op uw toepassing.

Zie [Core Video Playback bijhouden](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_track-core-vid-playback.html) voor een volledige lijst met gebeurtenissen voor videoanalyse.

1. Bepaal voor welke gebeurtenissen uw toepassing moet luisteren.

   * **Vereiste gebeurtenissen**: Luister naar alle afspeelgebeurtenissen.

      >[!IMPORTANT]
      >
      >De playbackgebeurtenis `MediaPlayerStatusChangeEvent.STATUS_CHANGE` verstrekt de spelerstatus, met inbegrip van fouten. Een van de staten kan de volgende stap van de speler beïnvloeden.

   * **Andere gebeurtenissen**: Optioneel, afhankelijk van uw toepassing.

      Als u bijvoorbeeld reclame in het afspelen opneemt, luistert u naar alle gebeurtenissen `AdBreakPlaybackEvent` en `AdPlaybackEvent`.

1. Implementeer gebeurtenislisteners voor elke gebeurtenis.

   TVSDK retourneert parameterwaarden aan uw callbacks van de gebeurtenislistener. Deze waarden bieden relevante informatie over de gebeurtenis die u in de listeners kunt gebruiken om de juiste handelingen uit te voeren.

   De `Event` klasse maakt een lijst van alle callback interfaces. Elke interface toont de parameters die voor die interface zijn teruggekeerd.

   Bijvoorbeeld:

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. Registreer uw callback luisteraars met het `MediaPlayer` voorwerp door `MediaPlayer.addEventListener` te gebruiken.

   `MediaPlayer` extends, dat onderdeel is van de kernbestanden van de Flash-speler en de functies  `flash.events.IEventDispatcher`en  `addEventListener`   `removeEventListener`bevat.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```


