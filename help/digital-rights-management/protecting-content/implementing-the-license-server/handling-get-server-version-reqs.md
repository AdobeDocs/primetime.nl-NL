---
title: Verzoeken om serverversie ophalen verwerken
description: Verzoeken om serverversie ophalen verwerken
copied-description: true
exl-id: 86a1bbe3-2ae4-4d4e-be51-fbbeb32147c8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Verzoeken om serverversie ophalen verwerken {#handle-get-server-version-requests}

Adobe Primetime DRM-client 3.0 of hoger verzendt een aanvraag voor een Get Server-versie om de mogelijkheden van de server te bepalen. Alle servers die Primetime DRM SDK 3.0 of later gebruiken moeten steun voor de verzoeken van de Versie van de Server van de Get uitvoeren.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* De aanvraag-URL moet &#39;Licentieserver-URL in metagegevens&#39; + &#39;zijn [!DNL /flashaccess/getServerVersion/v3]&quot;

Voor Primetime DRM SDK 4.0 of later, wijst het antwoord op een verzoek van de Versie van de Server van de Get aan cliënten erop dat de server versies 3 en 4 van het protocol Primetime DRM steunt.
