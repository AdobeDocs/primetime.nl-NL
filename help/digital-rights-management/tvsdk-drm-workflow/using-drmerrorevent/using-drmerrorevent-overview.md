---
seo-title: Het overzicht van de klasse DRMErrorEvent gebruiken
title: Het overzicht van de klasse DRMErrorEvent gebruiken
uuid: cbb9c1a7-3c50-479d-b7e5-63010a696dfa
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Het overzicht van de klasse DRMErrorEvent gebruiken {#using-the-drmerrorevent-class-overview}

Primetime verzendt een `DRMErrorEvent` object wanneer een Primetime-object, dat beveiligde inhoud probeert af te spelen, een [DRM-gerelateerde fout](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)aantreft. Als de gebruikersgegevens ongeldig zijn, wordt het `DRMAuthenticateEvent` object herhaaldelijk verzonden totdat de gebruiker geldige gegevens invoert of de toepassing geen nieuwe pogingen meer toestaat. De toepassing is verantwoordelijk voor het luisteren naar andere DRM-foutgebeurtenissen om de [DRM-gerelateerde fouten](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)te detecteren, identificeren en af te handelen.

Zelfs met geldige gebruikersgegevens kunnen de voorwaarden van de licentie voor de inhoud verhinderen dat een gebruiker de gecodeerde inhoud kan bekijken. Een gebruiker kan bijvoorbeeld de toegang worden geweigerd wanneer deze inhoud probeert weer te geven in een niet-geautoriseerde toepassing (bijv. de lijst Toepassingen toestaan). Een niet-geautoriseerde toepassing is een toepassing die niet is ondertekend met een toegelaten vermeld certificaat voor het ondertekenen van toepassingen. In dit geval wordt een `DRMErrorEvent` object verzonden.

Foutgebeurtenissen kunnen ook worden gegenereerd als de inhoud beschadigd is of als de versie van de toepassing niet overeenkomt met de versie die in de licentie is opgegeven. De toepassing moet een geschikt mechanisme bieden voor de afhandeling van fouten.
