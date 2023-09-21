---
description: In het gedeelte met meldingen van de TVSDK-bibliotheek van de browser kunt u een registratie- en foutopsporingssysteem maken dat nuttig kan zijn voor diagnose- en validatiedoeleinden.
title: Meldingssysteem
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Meldingssysteem {#notification-system}

In het gedeelte met meldingen van de TVSDK-bibliotheek van de browser kunt u een registratie- en foutopsporingssysteem maken dat nuttig kan zijn voor diagnose- en validatiedoeleinden.

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

Browser-TVSDK heeft een *no throw* beleid voor de API. De meeste methoden retourneren een `PSDKErrorCode` waarde om aan te geven of de methode is uitgevoerd. Voor een volledige lijst van alle mogelijke `PSDKErrorCode` waarden, zie de verwijzingen van TVSDK API van de Browser.

Asynchrone fouten worden via de specifieke gebeurtenissen op de hoogte gebracht.

TVSDK van browser verzendt `MediaPlayer` gebeurtenissen om informatie over speleractiviteit te geven. U moet gebeurtenislisteners implementeren om deze gebeurtenissen vast te leggen en erop te reageren.

>[!TIP]
>
>De zeer belangrijke gebeurtenissen en de informatie worden het programma geopend op de console van Webbrowser.

## Luisteren naar meldingen {#section_06B96633433D497E842FB7ADD5F2C7DA}

U kunt luisteren naar meldingen en uw eigen meldingen toevoegen aan de berichtgeschiedenis. De kern van het TVSDK-meldingssysteem van de browser is de `Notification` klasse, die een stand-alone bericht vertegenwoordigt.

Uw toepassing instellen om te luisteren naar meldingen:

1. Luister voor de statusveranderingen van MediaPlayer door de instantie te gebruiken MediaPlayer.

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implementeer de callback.

   De callback ontvangt een geval van `AdobePSDK.MediaPlayerStatusChangeEvent`en Browser-TVSDK geeft dit gebeurtenisobject door aan de callback die de nieuwe spelerstatus bevat.
1. Uw toepassing kan naar andere gebeurtenissen luisteren die door Browser TVSDK door Browser te gebruiken worden verzonden `MediaPlayer` -instantie.
