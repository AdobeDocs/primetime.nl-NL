---
seo-title: Verzoeken om verificatie verwerken
title: Verzoeken om verificatie verwerken
uuid: abcb9cf6-668e-405c-9659-9ed1bcc33024
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verzoeken om verificatie verwerken {#handle-authentication-requests}

De `AuthenticationHandler` klasse wordt gebruikt om authentificatieverzoeken te verwerken. Deze wordt alleen gebruikt voor verificatie van gebruikersnaam en wachtwoord.

Wanneer het produceren van het authentificatietoken, moet de symbolische vervaldatum worden gespecificeerd. Aangepaste eigenschappen kunnen ook in het token worden opgenomen. Indien ingesteld, zijn deze eigenschappen zichtbaar voor de server wanneer het verificatietoken wordt verzonden in volgende aanvragen. Zie [Vergunningsverzoeken](../../protecting-content/implementing-the-license-server/handling-license-reqs/license-handling-classes.md) voor informatie over de behandeling van de tokens van de douaneauthentificatie.

De manager leest een authentificatieverzoek en ontleedt het verzoekbericht wanneer `parseRequest()` wordt geroepen. De serverimplementatie onderzoekt de gebruikersreferenties in de aanvraag en als de referenties geldig zijn, genereert u een `AuthenticationToken` object door het aanroepen `getRequest().generateAuthToken()`. Als `AuthenticationRequestMessage.generateAuthToken()` niet eerder wordt aangeroepen `close()`, wordt een foutcode voor een verificatiefout verzonden.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot; [!DNL /flashaccess/authn/v4]&quot;. Als protocolversie 3 het maximum is dat door de client of server wordt ondersteund, sturen Adobe Primetime DRM-clients een verificatieaanvraag naar &quot;Licentieserver-URL in metagegevens&quot; + [!DNL /flashaccess/authn/v3]&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/authn/v1]&quot;

