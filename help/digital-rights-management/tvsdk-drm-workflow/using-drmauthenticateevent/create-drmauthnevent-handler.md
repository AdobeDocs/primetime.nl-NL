---
description: Het DRMAuthenticateEvent-object wordt verzonden wanneer een Primetime-object beveiligde inhoud wil afspelen waarvoor gebruikersverificatie is vereist voordat deze kan worden afgespeeld (en de verificatie is nog niet uitgevoerd). De DRMAuthenticateEvent-handler verzamelt de vereiste referenties (gebruikersnaam, wachtwoord en type) en geeft de waarden voor validatie door aan de methode .setDRMAuthenticationCredentials().
title: DRMAuthenticateEvent-handlers maken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# DRMAuthenticateEvent-handlers maken{#create-a-drmauthenticateevent-handler}

Het DRMAuthenticateEvent-object wordt verzonden wanneer een Primetime-object beveiligde inhoud wil afspelen waarvoor gebruikersverificatie is vereist voordat deze kan worden afgespeeld (en de verificatie is nog niet uitgevoerd). De DRMAuthenticateEvent-handler verzamelt de vereiste referenties (gebruikersnaam, wachtwoord en type) en geeft de waarden voor validatie door aan de methode .setDRMAuthenticationCredentials().

De toepassing moet over een mechanisme beschikken om gebruikersgegevens te verkrijgen. De toepassing kan bijvoorbeeld een eenvoudige gebruikersinterface voor het invoeren van de gebruikersnaam en het wachtwoord weergeven. Ook, zou het een mechanisme moeten verstrekken om herhaalde mislukkingspogingen van de authentificatie te behandelen en te beperken.

Maak een gebeurtenishandler die een set hard-coded verificatiegegevens doorgeeft aan het Primetime-object dat de gebeurtenis heeft gestart:

```
var connection:NetConnection = new NetConnection();  
connection.connect(null);  
var videoStream:Primetime = new Primetime(connection);  
 
videoStream.addEventListener( 
  DRMAuthenticateEvent.DRM_AUTHENTICATE,  
  drmAuthenticateEventHandler)  
  private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void {  
    videoStream.setDRMAuthenticationCredentials("administrator", "password", "drm");  
} 
```

(De code voor het afspelen van de video en het controleren of een verbinding met de videostream tot stand is gebracht, is hier niet opgenomen.)
