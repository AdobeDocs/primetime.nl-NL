---
title: Synchronisatieverzoeken afhandelen
description: Synchronisatieverzoeken afhandelen
copied-description: true
exl-id: b19245e3-19ae-4dd4-9e5e-6956feb91334
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# Synchronisatieverzoeken afhandelen {#handle-synchronization-requests}

Als een licentie synchronisatievereisten opgeeft  [Voorschriften voor synchronisatie](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) de client verzendt periodiek synchronisatieverzoeken naar de server op basis van de frequentie die in de licentie is opgegeven. Als u synchronisatieberichten wilt inschakelen, stelt u `SyncFrequencyRequirements` in een PlayRight.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot; [!DNL /flashaccess/sync/v4]&quot;. Anders is de aanvraag-URL &quot;License Server URL in metadata&quot; + &quot; [!DNL /flashaccess/sync/v3]&quot;

De synchronisatieberichten worden gebruikt om de tijd van de cliënt met de tijd van de server te synchroniseren. Als licenties zijn ingesloten in de inhoud en niet van een licentieserver hoeven te worden opgehaald, is het belangrijk dat de tijd van de client wordt gesynchroniseerd om te voorkomen dat de client de klok wijzigt om de licentievervaldatum te omzeilen.

De synchronisatieberichten kunnen ook worden gebruikt om de informatie van de cliëntstaat aan de server mee te delen ( `getClientState()`) voor terugdraaidetectie.

Zie [Terugdraaibeveiliging](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection).
