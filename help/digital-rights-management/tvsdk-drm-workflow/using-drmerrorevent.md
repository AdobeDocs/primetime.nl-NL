---
seo-title: Het overzicht van de klasse DRMErrorEvent gebruiken
title: Het overzicht van de klasse DRMErrorEvent gebruiken
uuid: cbb9c1a7-3c50-479d-b7e5-63010a696dfa
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# De klasse DRMErrorEvent gebruiken {#using-the-drmerrorevent-class}

Primetime verzendt een `DRMErrorEvent` object wanneer een Primetime-object, dat beveiligde inhoud probeert af te spelen, een [DRM-gerelateerde fout](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)aantreft. Als de gebruikersgegevens ongeldig zijn, wordt het `DRMAuthenticateEvent` object herhaaldelijk verzonden totdat de gebruiker geldige gegevens invoert of de toepassing geen nieuwe pogingen meer toestaat. De toepassing is verantwoordelijk voor het luisteren naar andere DRM-foutgebeurtenissen om de [DRM-gerelateerde fouten](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)te detecteren, identificeren en af te handelen.

Zelfs met geldige gebruikersgegevens kunnen de voorwaarden van de licentie voor de inhoud verhinderen dat een gebruiker de gecodeerde inhoud kan bekijken. Een gebruiker kan bijvoorbeeld de toegang worden geweigerd wanneer deze inhoud probeert weer te geven in een niet-geautoriseerde toepassing (bijv. whitelisting van toepassing). Een niet-geautoriseerde toepassing is een toepassing die niet is ondertekend met een gewhitelist handtekeningcertificaat voor de toepassing. In dit geval wordt een `DRMErrorEvent` object verzonden.

Foutgebeurtenissen kunnen ook worden gegenereerd als de inhoud beschadigd is of als de versie van de toepassing niet overeenkomt met de versie die in de licentie is opgegeven. De toepassing moet een geschikt mechanisme bieden voor de afhandeling van fouten.

## DRMErrorEvent-handlers maken {#create-a-drmerrorevent-handler}

Maak een gebeurtenishandler voor het verwerken van foutgebeurtenissen die vanaf Primetime worden verzonden wanneer een fout optreedt tijdens het afspelen van beveiligde inhoud.

Wanneer een toepassing een fout aantreft, wordt doorgaans een aantal opschoningstaken uitgevoerd. Vervolgens wordt de gebruiker op de hoogte gesteld van de fout en worden er opties geboden om het probleem op te lossen.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```
