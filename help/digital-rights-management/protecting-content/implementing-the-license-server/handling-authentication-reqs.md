---
title: Verzoeken om verificatie verwerken
description: Verzoeken om verificatie verwerken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Verzoeken om verificatie {#handle-authentication-requests} verwerken

De klasse `AuthenticationHandler` wordt gebruikt om authentificatieverzoeken te verwerken. Deze wordt alleen gebruikt voor verificatie van gebruikersnaam en wachtwoord.

Wanneer het produceren van het authentificatietoken, moet de symbolische vervaldatum worden gespecificeerd. Aangepaste eigenschappen kunnen ook in het token worden opgenomen. Indien ingesteld, zijn deze eigenschappen zichtbaar voor de server wanneer het verificatietoken wordt verzonden in volgende aanvragen. Zie [Vergunningsverzoeken verwerken](../../protecting-content/implementing-the-license-server/handling-license-reqs/license-handling-classes.md) voor informatie over het verwerken van aangepaste verificatietokens.

De manager leest een authentificatieverzoek en ontleedt het verzoekbericht wanneer `parseRequest()` wordt geroepen. De serverimplementatie onderzoekt de gebruikersgegevens in de aanvraag en als de gegevens geldig zijn, wordt een `AuthenticationToken`-object gegenereerd door `getRequest().generateAuthToken()` aan te roepen. Als `AuthenticationRequestMessage.generateAuthToken()` niet vóór `close()` wordt geroepen, wordt een de foutencode van de authentificatiefout verzonden.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot; [!DNL /flashaccess/authn/v4]&quot;. Als protocolversie 3 het maximum is dat door de client of server wordt ondersteund, sturen Adobe Primetime DRM-clients dan verificatieaanvragen naar &quot;Licentieserver in metagegevens&quot; + &quot; [!DNL /flashaccess/authn/v3]&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/authn/v1]&quot;

