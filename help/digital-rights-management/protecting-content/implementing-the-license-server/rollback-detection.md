---
title: Terugdraaidetectie
description: Terugdraaidetectie
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# Terugdraaidetectie {#rollback-detection}

Voor terugdraaiopsporing, vereisen sommige gebruiksregels de cliënt om staatsinformatie voor handhaving van de rechten te handhaven. Om bijvoorbeeld de gebruiksregel voor het afspeelvenster af te dwingen, slaat de client de datum en tijd op waarop de gebruiker de inhoud voor het eerst begon te bekijken. Deze gebeurtenis activeert het begin van het afspeelvenster. Als u het afspeelvenster veilig wilt afdwingen, moet de server ervoor zorgen dat de gebruiker geen back-up maakt van de client en deze status herstelt om de begintijd van het afspeelvenster die op de client is opgeslagen, te verwijderen. De server doet dit door de waarde van de terugdraaiteller van de cliënt te volgen.

Voor elk verzoek, krijgt de server de waarde van de teller door te roepen `RequestMessageBase.getClientState()` om `ClientState` object, vervolgens aanroepen `ClientState.getCounter()` om de huidige waarde van de cliëntstaatsteller te verkrijgen. Deze waarde moet door de server worden opgeslagen voor elke client (gebruik `MachineId.getUniqueId()` om de cliënt te identificeren verbonden aan de het terugschroeven van prijstellwaarde), en dan te roepen `ClientState.incrementCounter()` om de tellerwaarde met één te verhogen. Als de server detecteert dat de tellerwaarde lager is dan de laatste waarde die door de server wordt gezien, is de clientstatus mogelijk teruggedraaid.

Zie de `ClientState` API-naslagdocumentatie voor meer informatie over de detectie van knoeitoestand van clients.
