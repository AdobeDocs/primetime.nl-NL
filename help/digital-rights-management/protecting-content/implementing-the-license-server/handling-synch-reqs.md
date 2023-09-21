---
title: Synchronisatieverzoeken afhandelen
description: Synchronisatieverzoeken afhandelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# Synchronisatieverzoeken afhandelen {#handle-synchronization-requests}

Als een licentie synchronisatievereisten opgeeft  [Voorschriften voor synchronisatie](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) de client verzendt periodiek synchronisatieverzoeken naar de server op basis van de frequentie die in de licentie is opgegeven. Als u synchronisatieberichten wilt inschakelen, stelt u `SyncFrequencyRequirements` in een PlayRight.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Als het protocol versie 5 voor client- en serverondersteuning beide is, is de aanvraag-URL &quot;License Server URL in metadata: + &quot; [!DNL /flashaccess/sync/v4]&quot;. Anders is de aanvraag-URL &quot;License Server URL in metadata&quot; + &quot; [!DNL /flashaccess/sync/v3]&quot;

De synchronisatieberichten worden gebruikt om de tijd van de cliënt met de tijd van de server te synchroniseren. Als licenties zijn ingesloten in de inhoud en niet van een licentieserver hoeven te worden opgehaald, is het belangrijk dat de tijd van de client wordt gesynchroniseerd om te voorkomen dat de client de klok wijzigt om de licentievervaldatum te omzeilen.

De synchronisatieberichten kunnen ook worden gebruikt om de informatie van de cliëntstaat aan de server ( `getClientState()`) voor terugdraaidetectie.

Zie [Terugdraaibeveiliging](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection).
