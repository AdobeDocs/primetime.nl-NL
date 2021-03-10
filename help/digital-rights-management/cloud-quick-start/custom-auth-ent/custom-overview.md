---
title: Overzicht van aangepaste verificatie/machtiging (optioneel)
description: Overzicht van aangepaste verificatie/machtiging (optioneel)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# Overzicht van aangepaste verificatie/machtiging (optioneel){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM kan worden geconfigureerd om uw eigen Back-End-service voor verificatie/machtiging te bereiken om te bepalen:

* Mag deze gebruiker een licentie aanschaffen?
* Welke rechten/beperkingen moeten in de licentie worden opgenomen?

Primetime Cloud DRM bevat een referentie-implementatie van een back-end verificatie-/machtigingsservice. Voor demonstratiedoeleinden geeft deze server &quot;allow&quot;-antwoorden op BES-aanvragen. Zie [!DNL BEESServlet.java] om het servergedrag te wijzigen.

>[!NOTE]
>
>Eerder was dit een afzonderlijk product met de naam *Back End Entitlement Server* (BES), dus de verwijzingen naar BES in dit document en in de brondossiers.

