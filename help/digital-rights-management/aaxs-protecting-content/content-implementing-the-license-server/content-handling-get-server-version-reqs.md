---
title: Verzoeken om serverversie ophalen verwerken
description: Verzoeken om serverversie ophalen verwerken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Verzoeken voor ophalen serverversie worden verwerkt{#handling-get-server-version-requests}

De cliënt 3.0 van de Toegang van Adobe en verzenden hoger een Get verzoek van de Versie van de Server om de mogelijkheden van de server te bepalen. Alle servers die Adobe Access SDK 3.0 en hoger gebruiken, moeten ondersteuning implementeren voor de aanvragen voor de serverversie ophalen.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* De aanvraag-URL moet &#39;Licence Server URL in metadata&#39; + &#39;/flashaccess/getServerVersion/v3&#39; zijn

Voor Adobe Access SDK 4.0 en hoger geeft het antwoord op een aanvraag Server ophalen aan clients aan dat de server versie 3 en 4 van het Adobe Access-protocol ondersteunt.
