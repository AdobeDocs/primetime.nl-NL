---
title: Verzoeken om verificatie verwerken
description: Verzoeken om verificatie verwerken
copied-description: true
exl-id: c1d46ec0-e053-4824-b3b1-20320e259fbe
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Verzoeken om verificatie verwerken{#handling-authentication-requests}

De `AuthenticationHandler` klasse wordt gebruikt om authentificatieverzoeken te verwerken. Deze wordt alleen gebruikt voor verificatie van gebruikersnaam en wachtwoord.

Wanneer het produceren van het authentificatietoken, moet de symbolische vervaldatum worden gespecificeerd. Aangepaste eigenschappen kunnen ook in het token worden opgenomen. Indien ingesteld, zijn deze eigenschappen zichtbaar voor de server wanneer het verificatietoken wordt verzonden in volgende aanvragen. Zie [Vergunningsaanvragen afhandelen](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md) voor informatie over het verwerken van aangepaste verificatietokens.

De manager leest een authentificatieverzoek en ontleedt het verzoekbericht wanneer `parseRequest()` wordt aangeroepen. De serverimplementatie onderzoekt de gebruikersgegevens in het verzoek en als de gegevens geldig zijn, genereert een `AuthenticationToken` object aanroepen `getRequest().generateAuthToken()`. Indien `AuthenticationRequestMessage.generateAuthToken()` wordt niet eerder aangeroepen `close()`, wordt een foutcode voor een verificatiefout verzonden.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/authn/v4&quot;. Als protocolversie 3 het maximum is dat door of de cliënt of de server wordt gesteund, zullen de cliënten van de Toegang van Adobe naar &quot;de Server URL van de Vergunning in meta-gegevens&quot;verzenden + &quot;/flashaccess/authn/v3&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot;/flashaccess/authn/v1&quot;
