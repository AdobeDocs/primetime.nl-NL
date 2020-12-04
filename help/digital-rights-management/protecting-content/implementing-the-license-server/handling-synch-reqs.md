---
seo-title: Synchronisatieverzoeken afhandelen
title: Synchronisatieverzoeken afhandelen
uuid: e2623afb-7a57-402d-a8a1-07bcf6324d41
translation-type: tm+mt
source-git-commit: eed2ed2512c2c462cd43637d83d80bf9a5c0d490
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
