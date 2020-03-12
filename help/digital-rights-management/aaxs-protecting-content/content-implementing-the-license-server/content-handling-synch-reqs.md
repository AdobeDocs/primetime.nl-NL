---
seo-title: Synchronisatieverzoeken afhandelen
title: Synchronisatieverzoeken afhandelen
uuid: 37b2db09-4c09-4216-874b-b570a84569b6
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Synchronisatieverzoeken afhandelen{#handling-synchronization-requests}

. Als een licentie synchronisatievereisten opgeeft ([Vereisten voor Synchronisatie](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization)), zal de client regelmatig synchronisatieverzoeken naar de server verzenden op basis van de frequentie die in de licentie is opgegeven. Om synchronisatieberichten toe te laten, plaats SyncFrequencyRequirements in een PlayRight.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/sync/v4&quot;. Anders is de aanvraag-URL &quot;Licence Server URL in metadata&quot; + &quot;/flashaccess/sync/v3&quot;

De synchronisatieberichten worden gebruikt om de tijd van de cliënt met de tijd van de server te synchroniseren. Als licenties zijn ingesloten in de inhoud en niet van een licentieserver hoeven te worden opgehaald, is het belangrijk dat de tijd van de client wordt gesynchroniseerd om te voorkomen dat de client de klok wijzigt om de licentievervaldatum te omzeilen.

De berichten van de synchronisatie kunnen ook worden gebruikt om de informatie van de cliëntstaat aan de server ( `getClientState()`) voor terugschroeven van prijzenopsporing mee te delen. Zie [Terugdraaibeveiliging](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md).