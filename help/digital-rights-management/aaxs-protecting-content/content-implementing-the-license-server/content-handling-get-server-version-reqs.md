---
title: Verzoeken om serverversie ophalen verwerken
description: Verzoeken om serverversie ophalen verwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Verzoeken om serverversie ophalen verwerken{#handling-get-server-version-requests}

Client 3.0 en hoger van de Toegang van de Adobe verzenden een Get verzoek van de Versie van de Server om de mogelijkheden van de server te bepalen. Alle servers die de Toegang SDK 3.0 van de Adobe gebruiken en hoger moeten steun voor krijgen van de Versies van de Server uitvoeren.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* De aanvraag-URL moet &#39;Licence Server URL in metadata&#39; + &#39;/flashaccess/getServerVersion/v3&#39; zijn

Voor de Toegang van de Adobe SDK 4.0 en hoger, wijst het antwoord op een Get verzoek van de Versie van de Server aan cliënten erop dat de server versies 3 en 4 van het protocol van de Toegang van de Adobe steunt.
