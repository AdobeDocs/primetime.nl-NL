---
seo-title: Voorbeeld van clientverzoeken
title: Voorbeeld van clientverzoeken
uuid: 330d5e3c-1711-4375-bd11-e7702f0cde31
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Voorbeeld van clientverzoeken{#sample-client-requests}

U kunt een bibliotheek van de verzoeken van de steekproefcliënt verzamelen gebruikend hulpmiddelen zoals de Volmacht van Charles of Wireshark. U zou cliëntverzoeken moeten vangen nadat de server van de Individualisering opstelling is geweest, gebruikend de referentie van het Vervoer van de Individualisatie. U kunt deze cliëntverzoeken (via *krulling* of een ander hulpmiddel) dan verzenden naar het eindpunt van de Server van de Individualisatie om te verifiëren dat de server in gebruik behoorlijk is. Bijvoorbeeld:

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

U kunt deze verzoeken ook opnieuw verzenden na om het even welke veranderingen van de serverconfiguratie of updates ECI/CRL.

U zou de pagina van de Statistieken van Individualisatie met succesvolle individualisatietransacties ook moeten bijwerken.
