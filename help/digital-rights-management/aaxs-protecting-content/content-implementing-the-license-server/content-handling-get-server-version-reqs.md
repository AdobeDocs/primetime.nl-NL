---
seo-title: Verzoeken om serverversie ophalen verwerken
title: Verzoeken om serverversie ophalen verwerken
uuid: a3084faa-cf3d-45cc-a244-298308c4cf15
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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
