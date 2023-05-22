---
title: Het overzicht van de klasse DRMErrorEvent gebruiken
description: Het overzicht van de klasse DRMErrorEvent gebruiken
copied-description: true
exl-id: c651cdcf-f8f8-4085-a88e-d82030f90f11
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# De klasse DRMErrorEvent gebruiken {#using-the-drmerrorevent-class}

Primetime verzendt een `DRMErrorEvent` object wanneer een Primetime-object, dat beveiligde inhoud probeert af te spelen, een [DRM-gerelateerde fout](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages). Als de gebruikersgegevens ongeldig zijn, wordt `DRMAuthenticateEvent` herhaaldelijk wordt verzonden totdat de gebruiker geldige gegevens invoert of de toepassing geen nieuwe pogingen meer toestaat. De toepassing is verantwoordelijk voor het luisteren naar andere DRM-foutgebeurtenissen om de [DRM-gerelateerde fouten](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages).

Zelfs met geldige gebruikersgegevens kunnen de voorwaarden van de licentie voor de inhoud verhinderen dat een gebruiker de gecodeerde inhoud kan bekijken. Een gebruiker kan bijvoorbeeld de toegang worden geweigerd wanneer deze inhoud probeert weer te geven in een niet-geautoriseerde toepassing (bijv. de lijst Toepassingen toestaan). Een niet-geautoriseerde toepassing is een toepassing die niet is ondertekend met een toegelaten vermeld certificaat voor het ondertekenen van toepassingen. In dit geval `DRMErrorEvent` object wordt verzonden.

Foutgebeurtenissen kunnen ook worden gegenereerd als de inhoud beschadigd is of als de versie van de toepassing niet overeenkomt met de versie die in de licentie is opgegeven. De toepassing moet een geschikt mechanisme bieden voor de afhandeling van fouten.

## DRMErrorEvent-handlers maken {#create-a-drmerrorevent-handler}

Maak een gebeurtenishandler voor het verwerken van foutgebeurtenissen die vanaf Primetime worden verzonden wanneer een fout optreedt tijdens het afspelen van beveiligde inhoud.

Wanneer een toepassing een fout aantreft, wordt doorgaans een aantal opschoningstaken uitgevoerd. Vervolgens wordt de gebruiker op de hoogte gesteld van de fout en worden er opties geboden om het probleem op te lossen.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```
