---
title: Synchronisatieverzoeken afhandelen
description: Synchronisatieverzoeken afhandelen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Synchronisatieverzoeken {#handle-synchronization-requests} verwerken

Als voor een licentie synchronisatievereisten [Vereisten voor synchronisatie zijn opgegeven, ](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) verzendt de client periodiek synchronisatieverzoeken naar de server, op basis van de frequentie die in de licentie is opgegeven. Om synchronisatieberichten toe te laten, plaats `SyncFrequencyRequirements` in een PlayRight.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot; [!DNL /flashaccess/sync/v4]&quot;. Anders is de aanvraag-URL &quot;Licentieserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/sync/v3]&quot;

De synchronisatieberichten worden gebruikt om de tijd van de cliënt met de tijd van de server te synchroniseren. Als licenties zijn ingesloten in de inhoud en niet van een licentieserver hoeven te worden opgehaald, is het belangrijk dat de tijd van de client wordt gesynchroniseerd om te voorkomen dat de client de klok wijzigt om de licentievervaldatum te omzeilen.

De synchronisatieberichten kunnen ook worden gebruikt om de informatie van de cliëntstaat aan de server ( `getClientState()`) voor terugschroeven van prijzen mee te delen.

Zie [Terugdraaibeveiliging](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection).
