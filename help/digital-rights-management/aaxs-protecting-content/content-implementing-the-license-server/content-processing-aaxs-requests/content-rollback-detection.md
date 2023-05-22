---
title: Terugdraaidetectie
description: Terugdraaidetectie
copied-description: true
exl-id: 525ae64e-1ade-4661-8403-ee4e42181358
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Terugdraaidetectie{#rollback-detection}

Voor terugdraaiopsporing, vereisen sommige gebruiksregels de cliënt om staatsinformatie voor handhaving van de rechten te handhaven. Om bijvoorbeeld de gebruiksregel voor het afspeelvenster af te dwingen, slaat de client de datum en tijd op waarop de gebruiker de inhoud voor het eerst begon te bekijken. Deze gebeurtenis activeert het begin van het afspeelvenster. Om het afspeelvenster veilig af te dwingen, moet de server ervoor zorgen dat de gebruiker geen back-up maakt van de client en de status van de client herstelt om de begintijd van het afspeelvenster die op de client is opgeslagen, te verwijderen. De server doet dit door de waarde van de terugdraaiteller van de cliënt te volgen. Voor elk verzoek, krijgt de server de waarde van de teller door te roepen `RequestMessageBase.getClientState()` om `ClientState` object, vervolgens aanroepen `ClientState.getCounter()` om de huidige waarde van de cliëntstaatsteller te verkrijgen. Deze waarde moet door de server worden opgeslagen voor elke client (gebruik `MachineId.getUniqueId()` om de cliënt te identificeren verbonden aan de het terugschroeven van prijstellwaarde), en dan te roepen `ClientState.incrementCounter()` om de tellerwaarde met één te verhogen. Als de server detecteert dat de tellerwaarde lager is dan de laatste waarde die door de server wordt gezien, is de clientstatus mogelijk teruggedraaid. Zie voor meer informatie over de detectie van knoeien met de clientstatus de `ClientState` API-naslagdocumentatie.
