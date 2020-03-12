---
seo-title: Overzicht
title: Overzicht
uuid: d3bfa65b-2360-4843-b59e-71451fa62a2c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Overzicht{#overview}

Als u een licentie wilt aanvragen, verzendt de client de metagegevens die tijdens het verpakken in de inhoud zijn ingesloten. De licentieserver gebruikt de informatie in de metagegevens van de inhoud om een licentie te genereren.

De `LicenseHandler` leest een vergunningsverzoek en ontleedt het verzoek. `LicenseHandler`wordt uitgebreid `BatchHandlerBase` om aanvragen voor batchlicenties te kunnen verwerken, hoewel deze functie momenteel niet wordt ondersteund door Adobe Access-clients. De `getRequests()` methode retourneert een lijst met `LicenseRequestMessage` objecten. De aanroeper zou door `LicenseRequestMessages`, en voor elke aanvraag moeten herhalen, of een vergunning produceren of een foutencode plaatsen (zie de `LicenseRequestMessage` API verwijzingsdocumentatie voor details). Voor elke licentieaanvraag bepaalt de server of er een licentie wordt uitgegeven. Vraag `LicenseRequestMessage.getContentInfo()` om informatie te verkrijgen die uit de inhoudsmeta-gegevens, met inbegrip van inhoudsidentiteitskaart, vergunning ID, en beleid wordt gehaald.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/license/v4&quot;. Als protocolversie 3 het maximum is dat door de client of server wordt ondersteund, sturen Adobe Access-clients verificatieverzoeken naar &quot;Licentieserver voor metagegevens&quot; + &quot;/flashaccess/license/v3&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot;/flashaccess/license/v1&quot;

Als een fout optreedt tijdens het parseren van de aanvraag, `HandlerParsingException` wordt een fout gegenereerd. Deze uitzondering bevat foutinformatie die aan de client moet worden geretourneerd. Roep de foutinformatie op om deze op te halen `HandlerParsingException.getErrorData()`. Als een fout tijdens het genereren van een licentie optreedt omdat niet aan de beleidsvereisten is voldaan, `PolicyEvaluationException` wordt een fout gegenereerd. Deze uitzondering omvat ook `ErrorData` om aan de cliënt terug te keren. Zie de API-documentatie voor `LicenseRequestMessage.generateLicense()` meer informatie over de evaluatie van het beleid tijdens het genereren van licenties.

Licenties en fouten worden tegelijk verzonden wanneer `LicenseHandler.close()` deze worden aangeroepen.

Een apparaat kan meerdere licenties voor dezelfde inhoud hebben (dezelfde licentie-id), maar kan slechts één licentie voor een bepaalde licentie-id en beleids-id hebben. Als het een licentie ontvangt met een dubbele LicenseID/PolicyID, zal de nieuwe licentie de oude alleen vervangen als de uitgiftedatum van de nieuwe licentie later is dan de uitgiftedatum van de bestaande licentie. Deze logica wordt gebruikt om vergunningen te verwerken ingebed in inhoud, daarom wordt het niet geadviseerd om meer dan één vergunning met zelfde identiteitskaart van het Beleid in een brok van inhoud in te bedden. Dezelfde logica is van toepassing op licenties die via de `DRMManager.storeVoucher()` ActionScript3-API aan de client worden doorgegeven; als de klant al over een licentie met een latere uitgiftedatum beschikt, kan de opgegeven licentie worden genegeerd.
