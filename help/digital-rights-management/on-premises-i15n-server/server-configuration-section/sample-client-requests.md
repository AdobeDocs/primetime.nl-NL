---
title: Voorbeeld van clientverzoeken
description: Voorbeeld van clientverzoeken
copied-description: true
exl-id: 2b6a1349-aafc-4222-9081-525662f62961
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Voorbeeld van clientverzoeken{#sample-client-requests}

U kunt een bibliotheek van de verzoeken van de steekproefcliënt verzamelen gebruikend hulpmiddelen zoals de Volmacht van Charles of Wireshark. U zou cliëntverzoeken moeten vangen nadat de server van de Individualisering opstelling is geweest, gebruikend de referentie van het Vervoer van de Individualisatie. U kunt deze clientverzoeken vervolgens verzenden (via *krullen* of een ander hulpmiddel) aan het eindpunt van de Server van de Individualisatie om te verifiëren dat de server in gebruik behoorlijk is. Bijvoorbeeld:

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

U kunt deze verzoeken ook opnieuw verzenden na om het even welke veranderingen van de serverconfiguratie of updates ECI/CRL.

U zou de pagina van de Statistieken van Individualisatie met succesvolle individualisatietransacties ook moeten bijwerken.
