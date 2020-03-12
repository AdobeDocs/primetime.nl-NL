---
description: In het gedeelte met meldingen van de TVSDK-bibliotheek van de browser kunt u een registratie- en foutopsporingssysteem maken dat nuttig kan zijn voor diagnose- en validatiedoeleinden.
seo-description: In het gedeelte met meldingen van de TVSDK-bibliotheek van de browser kunt u een registratie- en foutopsporingssysteem maken dat nuttig kan zijn voor diagnose- en validatiedoeleinden.
seo-title: Meldingssysteem
title: Meldingssysteem
uuid: 69c4ff1d-3167-413b-ab49-942a5ddc34d7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Meldingssysteem {#notification-system}

In het gedeelte met meldingen van de TVSDK-bibliotheek van de browser kunt u een registratie- en foutopsporingssysteem maken dat nuttig kan zijn voor diagnose- en validatiedoeleinden.

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

Browser TVSDK heeft *geen beleid voor genereren* van zijn API. De meeste methoden retourneren een `PSDKErrorCode` waarde om aan te geven of de methode met succes is uitgevoerd. Voor een volledige lijst van alle mogelijke `PSDKErrorCode` waarden, zie Browser TVSDK API verwijzingen.

Asynchrone fouten worden via de specifieke gebeurtenissen op de hoogte gebracht.

Browser TVSDK verzendt `MediaPlayer` gebeurtenissen voor informatie over de speleractiviteit. U moet gebeurtenislisteners implementeren om deze gebeurtenissen vast te leggen en erop te reageren.

>[!TIP]
>
>De zeer belangrijke gebeurtenissen en de informatie worden het programma geopend op de console van Webbrowser.

## Luisteren naar meldingen {#section_06B96633433D497E842FB7ADD5F2C7DA}

U kunt luisteren naar meldingen en uw eigen meldingen toevoegen aan de berichtgeschiedenis. De kern van het Browser TVSDK berichtsysteem is de `Notification` klasse, die een stand-alone bericht vertegenwoordigt.

Uw toepassing instellen om te luisteren naar meldingen:

1. Luister voor de statusveranderingen van MediaPlayer door de instantie te gebruiken MediaPlayer.

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implementeer de callback.

   De callback ontvangt een instantie van de speler `AdobePSDK.MediaPlayerStatusChangeEvent`, en Browser TVSDK gaat dit gebeurtenisvoorwerp tot callback over die de nieuwe spelerstaat bevat.
1. Uw toepassing kan naar andere gebeurtenissen luisteren die door Browser TVSDK door de `MediaPlayer` instantie te gebruiken worden verzonden.

