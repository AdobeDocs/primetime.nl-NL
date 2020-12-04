---
seo-title: Terugdraaidetectie
title: Terugdraaidetectie
uuid: ec124bac-a1d7-45be-bf09-a99d5eec5042
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# Terugdraaidetectie {#rollback-detection}

Voor terugdraaiopsporing, vereisen sommige gebruiksregels de cliënt om staatsinformatie voor handhaving van de rechten te handhaven. Om bijvoorbeeld de gebruiksregel voor het afspeelvenster af te dwingen, slaat de client de datum en tijd op waarop de gebruiker de inhoud voor het eerst begon te bekijken. Deze gebeurtenis activeert het begin van het afspeelvenster. Als u het afspeelvenster veilig wilt afdwingen, moet de server ervoor zorgen dat de gebruiker geen back-up maakt van de client en deze status herstelt om de begintijd van het afspeelvenster die op de client is opgeslagen, te verwijderen. De server doet dit door de waarde van de terugdraaiteller van de cliënt te volgen.

Voor elke aanvraag krijgt de server de waarde van de teller door `RequestMessageBase.getClientState()` aan te roepen om het `ClientState`-object te verkrijgen en vervolgens `ClientState.getCounter()` aan te roepen om de huidige waarde van de client state-teller te verkrijgen. De server moet deze waarde opslaan voor elke client (gebruik `MachineId.getUniqueId()` om de client te identificeren die is gekoppeld aan de waarde van de terugdraaiteller) en roep `ClientState.incrementCounter()` vervolgens aan om de tegenwaarde met één te verhogen. Als de server detecteert dat de tellerwaarde lager is dan de laatste waarde die door de server wordt gezien, is de clientstatus mogelijk teruggedraaid.

Zie de `ClientState` API-naslagdocumentatie voor meer informatie over de detectie van knoeiboel op de client.
