---
seo-title: Synchronisatieverzoeken afhandelen
title: Synchronisatieverzoeken afhandelen
uuid: 37b2db09-4c09-4216-874b-b570a84569b6
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Synchronisatieverzoeken verwerken{#handling-synchronization-requests}

. Als een vergunning synchronisatievereisten ([Vereisten voor Synchronisatie](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization)) specificeert, zal de cliënt synchronisatieverzoeken aan de server periodiek verzenden, die op de frequentie wordt gebaseerd in de vergunning wordt gespecificeerd. Om synchronisatieberichten toe te laten, plaats SyncFrequencyRequirements in een PlayRight.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/sync/v4&quot;. Anders is de aanvraag-URL &quot;Licence Server URL in metadata&quot; + &quot;/flashaccess/sync/v3&quot;

De synchronisatieberichten worden gebruikt om de tijd van de cliënt met de tijd van de server te synchroniseren. Als licenties zijn ingesloten in de inhoud en niet van een licentieserver hoeven te worden opgehaald, is het belangrijk dat de tijd van de client wordt gesynchroniseerd om te voorkomen dat de client de klok wijzigt om de licentievervaldatum te omzeilen.

De synchronisatieberichten kunnen ook worden gebruikt om de informatie van de cliëntstaat aan de server ( `getClientState()`) voor terugschroeven van prijzen mee te delen. Zie [Terugdraaibeveiliging](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md).