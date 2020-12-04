---
description: Het DRMAuthenticateEvent-object wordt verzonden wanneer een Primetime-object beveiligde inhoud wil afspelen waarvoor gebruikersverificatie is vereist voordat deze kan worden afgespeeld (en de verificatie is nog niet uitgevoerd). De DRMAuthenticateEvent-handler verzamelt de vereiste referenties (gebruikersnaam, wachtwoord en type) en geeft de waarden voor validatie door aan de methode .setDRMAuthenticationCredentials().
seo-description: Het DRMAuthenticateEvent-object wordt verzonden wanneer een Primetime-object beveiligde inhoud wil afspelen waarvoor gebruikersverificatie is vereist voordat deze kan worden afgespeeld (en de verificatie is nog niet uitgevoerd). De DRMAuthenticateEvent-handler verzamelt de vereiste referenties (gebruikersnaam, wachtwoord en type) en geeft de waarden voor validatie door aan de methode .setDRMAuthenticationCredentials().
seo-title: DRMAuthenticateEvent-handlers maken
title: DRMAuthenticateEvent-handlers maken
uuid: 58330691-d0b5-46bd-9b1d-8dc597580d31
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Een DRMAuthenticateEvent-handler{#create-a-drmauthenticateevent-handler} maken

Het DRMAuthenticateEvent-object wordt verzonden wanneer een Primetime-object beveiligde inhoud wil afspelen waarvoor gebruikersverificatie is vereist voordat deze kan worden afgespeeld (en de verificatie is nog niet uitgevoerd). De DRMAuthenticateEvent-handler verzamelt de vereiste referenties (gebruikersnaam, wachtwoord en type) en geeft de waarden voor validatie door aan de methode .setDRMAuthenticationCredentials().

De toepassing moet over een mechanisme beschikken om gebruikersgegevens te verkrijgen. De toepassing kan bijvoorbeeld een eenvoudige gebruikersinterface voor het invoeren van gebruikersnaam en wachtwoord weergeven. Ook, zou het een mechanisme moeten verstrekken om herhaalde mislukkingspogingen van de authentificatie te behandelen en te beperken.

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
