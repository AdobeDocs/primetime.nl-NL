---
title: Verzoeken om serverversie ophalen verwerken
description: Verzoeken om serverversie ophalen verwerken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Verzoeken om serverversie ophalen verwerken {#handle-get-server-version-requests}

Adobe Primetime DRM-client 3.0 of hoger verzendt een aanvraag voor een Get Server-versie om de mogelijkheden van de server te bepalen. Alle servers die Primetime DRM SDK 3.0 of later gebruiken moeten steun voor de verzoeken van de Versie van de Server van de Get uitvoeren.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* De aanvraag-URL moet &#39;Licence Server URL in metadata&#39; + &#39; [!DNL /flashaccess/getServerVersion/v3]&#39; zijn

Voor Primetime DRM SDK 4.0 of later, wijst het antwoord op een verzoek van de Versie van de Server van de Get aan cliënten erop dat de server versies 3 en 4 van het protocol Primetime DRM steunt.
