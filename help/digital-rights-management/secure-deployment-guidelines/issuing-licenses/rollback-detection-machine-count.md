---
description: Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan die met de gebruiker worden geassocieerd.
seo-description: Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan die met de gebruiker worden geassocieerd.
seo-title: Aantal machines bij afgifte van vergunningen
title: Aantal machines bij afgifte van vergunningen
uuid: 7ba8a8d4-a31f-4f37-82a7-755cfa443544
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Aantal machines bij afgifte van vergunningen {#machine-count-when-issuing-licenses}

Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan die met de gebruiker worden geassocieerd.

De meest robuuste manier om machine IDs te volgen is de waarde op te slaan die door de [MachineId.getBytes ()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) methode in een gegevensbestand is teruggekeerd. Wanneer een nieuwe aanvraag wordt ontvangen, vergelijkt u de machine-id in de aanvraag met de bekende machine-id&#39;s met [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) voert een vergelijking van id&#39;s uit om te bepalen of de id&#39;s dezelfde computer vertegenwoordigen. Deze vergelijking is alleen praktisch als er een klein aantal machine-id&#39;s is. Als gebruikers bijvoorbeeld vijf computers in hun domein mogen hebben, kunt u in de database zoeken naar de machine-id&#39;s die aan de gebruikersnaam van de gebruiker zijn gekoppeld en een kleine set gegevens ter vergelijking verkrijgen.

Deze vergelijking is niet praktisch voor plaatsingen die anonieme toegang toestaan. In dit geval kan [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) worden gebruikt. Deze id kan echter niet hetzelfde zijn als de gebruiker toegang krijgt tot inhoud van Flash en Adobe AIR®-runtimes.

>[!NOTE]
>
>De id overblijft niet als de gebruiker de vaste schijf opnieuw formatteert.