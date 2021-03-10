---
description: In het gedeelte met meldingen van de TVSDK-bibliotheek van de browser kunt u een registratie- en foutopsporingssysteem maken dat nuttig kan zijn voor diagnose- en validatiedoeleinden.
title: Meldingssysteem
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Meldingssysteem {#notification-system}

In het gedeelte met meldingen van de TVSDK-bibliotheek van de browser kunt u een registratie- en foutopsporingssysteem maken dat nuttig kan zijn voor diagnose- en validatiedoeleinden.

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

Browser TVSDK heeft een *geen beleid throw* voor zijn API. De meeste methoden retourneren een waarde `PSDKErrorCode` om aan te geven of de methode met succes is uitgevoerd. Voor een volledige lijst van alle mogelijke `PSDKErrorCode` waarden, zie Browser TVSDK API verwijzingen.

Asynchrone fouten worden via de specifieke gebeurtenissen op de hoogte gebracht.

Browser-TVSDK verzendt `MediaPlayer`-gebeurtenissen om informatie te verschaffen over de activiteit van de speler. U moet gebeurtenislisteners implementeren om deze gebeurtenissen vast te leggen en erop te reageren.

>[!TIP]
>
>De zeer belangrijke gebeurtenissen en de informatie worden het programma geopend op de console van Webbrowser.

## Luisteren naar berichten {#section_06B96633433D497E842FB7ADD5F2C7DA}

U kunt luisteren naar meldingen en uw eigen meldingen toevoegen aan de berichtgeschiedenis. De kern van het Browser TVSDK berichtsysteem is de `Notification` klasse, die een stand-alone bericht vertegenwoordigt.

Uw toepassing instellen om te luisteren naar meldingen:

1. Luister voor de statusveranderingen van MediaPlayer door de instantie te gebruiken MediaPlayer.

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. Implementeer de callback.

   De callback ontvangt een geval van `AdobePSDK.MediaPlayerStatusChangeEvent`, en Browser TVSDK gaat dit gebeurtenisvoorwerp tot callback over die de nieuwe spelerstaat bevat.
1. Uw toepassing kan naar andere gebeurtenissen luisteren die door Browser TVSDK door de `MediaPlayer` instantie te gebruiken worden verzonden.

