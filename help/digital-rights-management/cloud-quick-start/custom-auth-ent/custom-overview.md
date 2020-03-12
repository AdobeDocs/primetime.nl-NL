---
seo-title: Overzicht van aangepaste verificatie/machtiging (optioneel)
title: Overzicht van aangepaste verificatie/machtiging (optioneel)
uuid: 8b5e38a5-562c-4781-ac40-4b3d6cdd97fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht van aangepaste verificatie/machtiging (optioneel){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM kan worden geconfigureerd om uw eigen Back-End-service voor verificatie/machtiging te bereiken om te bepalen:

* Mag deze gebruiker een licentie aanschaffen?
* Welke rechten/beperkingen moeten in de licentie worden opgenomen?

Primetime Cloud DRM bevat een referentie-implementatie van een back-end verificatie-/machtigingsservice. Voor demonstratiedoeleinden geeft deze server &quot;allow&quot;-antwoorden op BES-aanvragen. Zie [!DNL BEESServlet.java] het servergedrag wijzigen.

>[!NOTE]
>
>Eerder, was dit een afzonderlijk product genoemd de Server *van de Toestemming van het Eind van de* Achterkant (BEES), zo de verwijzingen naar BEES door dit document en in de brondossiers.

