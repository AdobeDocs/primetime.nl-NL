---
title: Verzoeken om serverversie ophalen verwerken
description: Verzoeken om serverversie ophalen verwerken
copied-description: true
exl-id: 125b0111-17e9-4f6f-954b-6975048cd2fa
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Verzoeken om serverversie ophalen verwerken{#handling-get-server-version-requests}

De cliënt 3.0 van de Toegang van Adobe en verzenden hoger een Get verzoek van de Versie van de Server om de mogelijkheden van de server te bepalen. Alle servers die Adobe Access SDK 3.0 en hoger gebruiken, moeten ondersteuning implementeren voor de aanvragen voor de serverversie ophalen.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* De aanvraag-URL moet &#39;Licence Server URL in metadata&#39; + &#39;/flashaccess/getServerVersion/v3&#39; zijn

Voor Adobe Access SDK 4.0 en hoger geeft het antwoord op een aanvraag Server ophalen aan clients aan dat de server versie 3 en 4 van het Adobe Access-protocol ondersteunt.
