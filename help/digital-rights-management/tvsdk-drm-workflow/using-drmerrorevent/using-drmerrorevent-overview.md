---
title: Het overzicht van de klasse DRMErrorEvent gebruiken
description: Het overzicht van de klasse DRMErrorEvent gebruiken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Overzicht van de DRMErrorEvent-klasse gebruiken {#using-the-drmerrorevent-class-overview}

Primetime verzendt een `DRMErrorEvent` voorwerp wanneer een voorwerp Primetime, die probeert om beschermde inhoud te spelen, een [DRM-verwante fout](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) ontmoet. Als de gebruikersgegevens ongeldig zijn, verzendt het object `DRMAuthenticateEvent` herhaaldelijk totdat de gebruiker geldige gegevens invoert of de toepassing geen nieuwe pogingen meer toestaat. De toepassing is verantwoordelijk voor het luisteren naar andere DRM-foutgebeurtenissen om de [DRM-gerelateerde fouten](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) te detecteren, identificeren en af te handelen.

Zelfs met geldige gebruikersgegevens kunnen de voorwaarden van de licentie voor de inhoud verhinderen dat een gebruiker de gecodeerde inhoud kan bekijken. Een gebruiker kan bijvoorbeeld de toegang worden geweigerd wanneer deze inhoud probeert weer te geven in een niet-geautoriseerde toepassing (bijv. de lijst Toepassingen toestaan). Een niet-geautoriseerde toepassing is een toepassing die niet is ondertekend met een toegelaten vermeld certificaat voor het ondertekenen van toepassingen. In dit geval wordt een `DRMErrorEvent`-object verzonden.

Foutgebeurtenissen kunnen ook worden gegenereerd als de inhoud beschadigd is of als de versie van de toepassing niet overeenkomt met de versie die in de licentie is opgegeven. De toepassing moet een geschikt mechanisme bieden voor de afhandeling van fouten.
