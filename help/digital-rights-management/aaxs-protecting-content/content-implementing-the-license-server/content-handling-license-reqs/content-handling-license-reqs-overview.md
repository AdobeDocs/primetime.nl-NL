---
seo-title: Overzicht
title: Overzicht
uuid: d3bfa65b-2360-4843-b59e-71451fa62a2c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Overzicht{#overview}

Als u een licentie wilt aanvragen, verzendt de client de metagegevens die tijdens het verpakken in de inhoud zijn ingesloten. De licentieserver gebruikt de informatie in de metagegevens van de inhoud om een licentie te genereren.

`LicenseHandler` leest een vergunningsverzoek en ontleedt het verzoek. `LicenseHandler`breidt zich  `BatchHandlerBase` uit om partijvergunningsverzoeken aan te passen, hoewel deze eigenschap momenteel niet door de cliënten van Adobe Access wordt gesteund. De methode `getRequests()` retourneert een lijst met `LicenseRequestMessage`-objecten. De aanroeper zou door `LicenseRequestMessages` moeten herhalen, en voor elk verzoek, of een vergunning produceren of een foutencode plaatsen (zie de `LicenseRequestMessage` API verwijzingsdocumentatie voor details). Voor elke licentieaanvraag bepaalt de server of er een licentie wordt uitgegeven. Roep `LicenseRequestMessage.getContentInfo()` aan om informatie te verkrijgen die uit de inhoudsmeta-gegevens, met inbegrip van inhoudsidentiteitskaart, vergunning ID, en beleid wordt gehaald.

* De klasse van de verzoekmanager is `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* De klasse van het verzoekbericht is `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* Als zowel de client als het serverondersteuningsprotocol versie 5, is de aanvraag-URL &quot;Licence Server URL in metadata: + &quot;/flashaccess/license/v4&quot;. Als protocolversie 3 het maximum is dat door of de cliënt of de server wordt gesteund, zullen de cliënten van de Toegang van Adobe naar &quot;de Server URL van de Vergunning in meta-gegevens&quot;verzenden + &quot;/flashaccess/license/v3&quot;. Anders worden verificatieaanvragen verzonden naar &quot;Licentieserver-URL in metagegevens&quot; + &quot;/flashaccess/license/v1&quot;

Als een fout tijdens het ontleden van het verzoek voorkomt, wordt `HandlerParsingException` geworpen. Deze uitzondering bevat foutinformatie die aan de client moet worden geretourneerd. Om de fouteninformatie terug te winnen, roep `HandlerParsingException.getErrorData()`. Als tijdens het genereren van een licentie een fout optreedt omdat niet aan de beleidsvereisten is voldaan, wordt een `PolicyEvaluationException` gegenereerd. Deze uitzondering omvat ook `ErrorData` die naar de client moet worden geretourneerd. Zie de API-documentatie voor `LicenseRequestMessage.generateLicense()` voor meer informatie over de evaluatie van het beleid tijdens het genereren van licenties.

Licenties en fouten worden tegelijk verzonden wanneer `LicenseHandler.close()` wordt aangeroepen.

Een apparaat kan meerdere licenties voor dezelfde inhoud hebben (dezelfde licentie-id), maar kan slechts één licentie voor een bepaalde licentie-id en beleids-id hebben. Als het een licentie ontvangt met een dubbele LicenseID/PolicyID, zal de nieuwe licentie de oude alleen vervangen als de uitgiftedatum van de nieuwe licentie later is dan de uitgiftedatum van de bestaande licentie. Deze logica wordt gebruikt om vergunningen te verwerken ingebed in inhoud, daarom wordt het niet geadviseerd om meer dan één vergunning met zelfde identiteitskaart van het Beleid in een brok van inhoud in te bedden. Dezelfde logica geldt voor licenties die via de ActionScript3-API `DRMManager.storeVoucher()` aan de client worden doorgegeven; als de klant al over een licentie met een latere uitgiftedatum beschikt, kan de opgegeven licentie worden genegeerd.
