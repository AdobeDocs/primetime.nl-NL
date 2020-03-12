---
description: Vanaf het moment dat de instantie MediaPlayer wordt gemaakt tot het moment dat deze wordt beëindigd, gaat deze instantie van het ene frame naar het volgende.
seo-description: Vanaf het moment dat de instantie MediaPlayer wordt gemaakt tot het moment dat deze wordt beëindigd, gaat deze instantie van het ene frame naar het volgende.
seo-title: Levenscyclus en status van het MediaPlayer-object
title: Levenscyclus en status van het MediaPlayer-object
uuid: fe76ea80-aaa8-43bc-9b81-85e0551f70dd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Levenscyclus en status van het MediaPlayer-object{#life-cycle-and-states-of-the-mediaplayer-object}

Vanaf het moment dat de instantie MediaPlayer wordt gemaakt tot het moment dat deze wordt beëindigd, gaat deze instantie van het ene frame naar het volgende.

Hier volgen de mogelijke staten:

* **IDLE**: `MediaPlayerStatus.IDLE`

* **INITIALISEREN**: `MediaPlayerStatus.INITIALIZING`

* **GEÏNITIALISEERD**: `MediaPlayerStatus.INITIALIZED`

* **VOORBEREIDEN**: `MediaPlayerStatus.PREPARING`

* **BEREID**: `MediaPlayerStatus.PREPARED`

* **AFSPELEN**: `MediaPlayerStatus.PLAYING`

* **GEPAUZEERD**: `MediaPlayerStatus.PAUSED`

* **ZOEKEN**: `MediaPlayerStatus.SEEKING`

* **VOLTOOID**: `MediaPlayerStatus.COMPLETE`

* **FOUT**: `MediaPlayerStatus.ERROR`

* **UITGEGEVEN**: `MediaPlayerStatus.RELEASED`

De volledige lijst met staten wordt gedefinieerd in `MediaPlayerStatus`.

Het is handig om te weten wat de status van de speler is, omdat bepaalde bewerkingen alleen zijn toegestaan als de speler zich in een bepaalde status bevindt. Kan bijvoorbeeld `play` niet worden aangeroepen in de status IDLE. Het moet worden opgeroepen nadat de staat PREPARED is bereikt. De staat ERROR verandert ook wat daarna kan gebeuren.

Wanneer een mediabron wordt geladen en afgespeeld, gaat de speler als volgt over:

1. De beginstaat is IDLE.
1. Uw toepassing roept `MediaPlayer.replaceCurrentResource`op, waardoor de speler naar de status INITIALIZING wordt verplaatst.
1. Als de bron is geladen in Browser-TVSDK, verandert de status in INITIALIZED.
1. Uw toepassingsvraag `MediaPlayer.prepareToPlay`, en de staat verandert in PREPARING.
1. Browser-TVSDK bereidt de mediastream voor en start de bewerking en invoeging van de advertentie (indien ingeschakeld).

   Wanneer deze stap is voltooid, worden advertenties ingevoegd in de tijdlijn of is de advertentieprocedure mislukt en verandert de spelerstatus in PREPARED.
1. Terwijl de toepassing de media afspeelt en pauzeert, wordt de status verplaatst tussen AFSPELEN en GEPAUZEERD.

   >[!TIP]
   >
   >Tijdens het afspelen of pauzeren, wanneer u weg navigeert van het afspelen, het apparaat sluit of van toepassing verandert, verandert de staat in GESUSPENDED en de middelen worden vrijgegeven. Herstel de mediaspeler om door te gaan.

1. Wanneer de speler het einde van de stream bereikt, wordt de status COMPLETE.
1. Wanneer uw toepassing de mediaspeler loslaat, verandert de status in RELEASED.
1. Als er tijdens het proces een fout optreedt, verandert de status in ERROR.

Hier volgt een voorbeeld van de levenscyclus van een instantie MediaPlayer:

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

U kunt de status gebruiken om feedback te geven aan de gebruiker over het proces (bijvoorbeeld een spinner in afwachting van de volgende statuswijziging) of om de volgende stappen uit te voeren in het afspelen van de media, zoals wachten op de juiste status voordat u de volgende methode aanroept.

Bijvoorbeeld:

```js
function onStateChanged(state) { 
    switch(state) { 
        // It is recommended that you call prepareToPlay()  
        // after receiving the INITIALIZED state             
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            mediaPlayer.prepareToPlay(); 
            break; 
    } 
} 
```

