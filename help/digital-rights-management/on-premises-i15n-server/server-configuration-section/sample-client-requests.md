---
title: Voorbeeld van clientverzoeken
description: Voorbeeld van clientverzoeken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---


# Voorbeeld van clientverzoeken{#sample-client-requests}

U kunt een bibliotheek van de verzoeken van de steekproefcliënt verzamelen gebruikend hulpmiddelen zoals de Volmacht van Charles of Wireshark. U zou cliëntverzoeken moeten vangen nadat de server van de Individualisering opstelling is geweest, gebruikend de referentie van het Vervoer van de Individualisatie. Vervolgens kunt u deze clientverzoeken (via *curl* of een ander gereedschap) naar het eindpunt van de Individualization-server verzenden om te controleren of de server op de juiste wijze wordt uitgevoerd. Bijvoorbeeld:

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

U kunt deze verzoeken ook opnieuw verzenden na om het even welke veranderingen van de serverconfiguratie of updates ECI/CRL.

U zou de pagina van de Statistieken van Individualisatie met succesvolle individualisatietransacties ook moeten bijwerken.
