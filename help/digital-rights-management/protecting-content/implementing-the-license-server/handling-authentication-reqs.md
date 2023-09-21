---
title: Verzoeken om verificatie verwerken
description: Verzoeken om verificatie verwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Verzoeken om verificatie verwerken {#handle-authentication-requests}

De `AuthenticationHandler` klasse wordt gebruikt om authentificatieverzoeken te verwerken. Deze wordt alleen gebruikt voor verificatie van gebruikersnaam en wachtwoord.

Wanneer het produceren van het authentificatietoken, moet de symbolische vervaldatum worden gespecificeerd. Aangepaste eigenschappen kunnen ook in het token worden opgenomen. Indien ingesteld, zijn deze eigenschappen zichtbaar voor de server wanneer het verificatietoken wordt verzonden in volgende aanvragen. Zie [Vergunningsaanvragen afhandelen](../../protecting-content/implementing-the-license-server/handling-license-reqs/license-handling-classes.md) voor informatie over het verwerken van aangepaste verificatietokens.

De manager leest een authentificatieverzoek en ontleedt het verzoekbericht wanneer `parseRequest()` wordt aangeroepen. De serverimplementatie onderzoekt de gebruikersgegevens in het verzoek en als de gegevens geldig zijn, genereert een `AuthenticationToken` object aanroepen `getRequest().generateAuthToken()`. Indien `AuthenticationRequestMessage.generateAuthToken()` wordt niet eerder aangeroepen `close()`, wordt een foutcode voor een verificatiefout verzonden.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Als het protocol versie 5 voor client- en serverondersteuning beide is, is de aanvraag-URL &quot;License Server URL in metadata: + &quot; [!DNL /flashaccess/authn/v4]&quot;. Als protocolversie 3 het maximum is dat door de client of server wordt ondersteund, sturen Adobe Primetime DRM-clients dan verificatieaanvragen naar &quot;Licentie Server URL in metadata&quot; + &quot; [!DNL /flashaccess/authn/v3]&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/authn/v1]&quot;
