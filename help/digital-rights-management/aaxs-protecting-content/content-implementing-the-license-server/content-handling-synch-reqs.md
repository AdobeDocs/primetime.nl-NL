---
title: Synchronisatieverzoeken afhandelen
description: Synchronisatieverzoeken afhandelen
copied-description: true
exl-id: bbfc6096-72df-4597-96b3-8f67a640ea8f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Synchronisatieverzoeken afhandelen{#handling-synchronization-requests}

. Als een licentie synchronisatievereisten opgeeft ([Voorschriften voor synchronisatie](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization)), verzendt de client periodiek synchronisatieverzoeken naar de server op basis van de frequentie die in de licentie is opgegeven. Om synchronisatieberichten toe te laten, plaats SyncFrequencyRequirements in een PlayRight.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/sync/v4&quot;. Anders is de aanvraag-URL &quot;Licence Server URL in metadata&quot; + &quot;/flashaccess/sync/v3&quot;

De synchronisatieberichten worden gebruikt om de tijd van de cliënt met de tijd van de server te synchroniseren. Als licenties zijn ingesloten in de inhoud en niet van een licentieserver hoeven te worden opgehaald, is het belangrijk dat de tijd van de client wordt gesynchroniseerd om te voorkomen dat de client de klok wijzigt om de licentievervaldatum te omzeilen.

De synchronisatieberichten kunnen ook worden gebruikt om de informatie van de cliëntstaat aan de server mee te delen ( `getClientState()`) voor terugdraaidetectie. Zie [Terugdraaibeveiliging](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md).
