---
description: Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan die met de gebruiker worden geassocieerd.
title: Aantal machines bij afgifte van vergunningen
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Aantal machines bij afgifte van vergunningen {#machine-count-when-issuing-licenses}

Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan die met de gebruiker worden geassocieerd.

De meest robuuste manier om machine IDs te volgen is de waarde op te slaan die door wordt teruggekeerd [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) in een database. Wanneer een nieuw verzoek wordt ontvangen, vergelijk machine-id in het verzoek met bekende machine-id&#39;s door [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) voert een vergelijking van id&#39;s uit om te bepalen of de id&#39;s dezelfde computer vertegenwoordigen. Deze vergelijking is alleen praktisch als er een klein aantal machine-id&#39;s is. Als gebruikers bijvoorbeeld vijf computers in hun domein mogen hebben, kunt u in de database zoeken naar de machine-id&#39;s die aan de gebruikersnaam van de gebruiker zijn gekoppeld en een kleine set gegevens ter vergelijking verkrijgen.

Deze vergelijking is niet praktisch voor plaatsingen die anonieme toegang toestaan. In dit geval: [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) kan worden gebruikt. Deze id kan echter niet hetzelfde zijn als de gebruiker toegang heeft tot inhoud van Flash- en Adobe AIR®-runtimes.

>[!NOTE]
>
>De id overblijft niet als de gebruiker de vaste schijf opnieuw formatteert.