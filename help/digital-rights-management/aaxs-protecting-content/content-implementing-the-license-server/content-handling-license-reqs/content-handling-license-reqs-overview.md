---
title: Overzicht
description: Overzicht
copied-description: true
exl-id: f1a55d5c-c7df-4b8f-8c1e-875d30026069
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Overzicht{#overview}

Als u een licentie wilt aanvragen, verzendt de client de metagegevens die tijdens het verpakken in de inhoud zijn ingesloten. De licentieserver gebruikt de informatie in de metagegevens van de inhoud om een licentie te genereren.

De `LicenseHandler` leest een vergunningsverzoek en ontleedt het verzoek. `LicenseHandler`extends `BatchHandlerBase` om partijvergunningsverzoeken aan te passen, hoewel deze eigenschap momenteel niet door de cliënten van Adobe Access wordt gesteund. De `getRequests()` methode retourneert een lijst met `LicenseRequestMessage` objecten. De bezoeker zou door moeten herhalen `LicenseRequestMessages`en voor elke aanvraag een licentie genereren of een foutcode instellen (zie de `LicenseRequestMessage` API-naslagdocumentatie voor meer informatie). Voor elke licentieaanvraag bepaalt de server of er een licentie wordt uitgegeven. Bellen `LicenseRequestMessage.getContentInfo()` om informatie op te halen uit de metagegevens van de inhoud, zoals de inhoud-id, licentie-id en het beleid.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/license/v4&quot;. Als protocolversie 3 het maximum is dat door of de cliënt of de server wordt gesteund, zullen de cliënten van de Toegang van Adobe naar &quot;de Server URL van de Vergunning in meta-gegevens&quot;verzenden + &quot;/flashaccess/license/v3&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot;/flashaccess/license/v1&quot;

Als een fout optreedt tijdens het parseren van de aanvraag, `HandlerParsingException` wordt gegenereerd. Deze uitzondering bevat foutinformatie die aan de client moet worden geretourneerd. Om de fouteninformatie terug te winnen, roep `HandlerParsingException.getErrorData()`. Als een fout optreedt tijdens het genereren van een licentie omdat niet aan de beleidsvereisten is voldaan, kan een `PolicyEvaluationException` wordt gegenereerd. Deze uitzondering omvat ook `ErrorData` aan de client worden geretourneerd. Zie de API-documentatie voor `LicenseRequestMessage.generateLicense()` voor details over hoe het beleid tijdens vergunningsproductie wordt geëvalueerd.

Licenties en fouten worden tegelijk verzonden `LicenseHandler.close()` wordt aangeroepen.

Een apparaat kan meerdere licenties voor dezelfde inhoud hebben (dezelfde licentie-id), maar kan slechts één licentie voor een bepaalde licentie-id en beleids-id hebben. Als het een licentie ontvangt met een dubbele LicenseID/PolicyID, zal de nieuwe licentie de oude alleen vervangen als de uitgiftedatum van de nieuwe licentie later is dan de uitgiftedatum van de bestaande licentie. Deze logica wordt gebruikt om vergunningen te verwerken ingebed in inhoud, daarom wordt het niet geadviseerd om meer dan één vergunning met zelfde identiteitskaart van het Beleid in een brok van inhoud in te bedden. Dezelfde logica geldt voor licenties die via de `DRMManager.storeVoucher()` ActionScript3 API; als de klant al over een licentie met een latere uitgiftedatum beschikt, kan de opgegeven licentie worden genegeerd.
