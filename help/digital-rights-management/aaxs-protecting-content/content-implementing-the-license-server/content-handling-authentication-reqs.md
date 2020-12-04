---
seo-title: Verzoeken om verificatie verwerken
title: Verzoeken om verificatie verwerken
uuid: 036582d4-611c-4772-b247-81a3144fd5d6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# Verzoeken voor verificatie worden verwerkt{#handling-authentication-requests}

De klasse `AuthenticationHandler` wordt gebruikt om authentificatieverzoeken te verwerken. Deze wordt alleen gebruikt voor verificatie van gebruikersnaam en wachtwoord.

Wanneer het produceren van het authentificatietoken, moet de symbolische vervaldatum worden gespecificeerd. Aangepaste eigenschappen kunnen ook in het token worden opgenomen. Indien ingesteld, zijn deze eigenschappen zichtbaar voor de server wanneer het verificatietoken wordt verzonden in volgende aanvragen. Zie [Vergunningsverzoeken verwerken](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md) voor informatie over het verwerken van aangepaste verificatietokens.

De manager leest een authentificatieverzoek en ontleedt het verzoekbericht wanneer `parseRequest()` wordt geroepen. De serverimplementatie onderzoekt de gebruikersgegevens in de aanvraag en als de gegevens geldig zijn, wordt een `AuthenticationToken`-object gegenereerd door `getRequest().generateAuthToken()` aan te roepen. Als `AuthenticationRequestMessage.generateAuthToken()` niet vóór `close()` wordt geroepen, wordt een de foutencode van de authentificatiefout verzonden.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/authn/v4&quot;. Als protocolversie 3 het maximum is dat door of de cliënt of de server wordt gesteund, zullen de cliënten van de Toegang van Adobe naar &quot;de Server URL van de Vergunning in meta-gegevens&quot;verzenden + &quot;/flashaccess/authn/v3&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot;/flashaccess/authn/v1&quot;

