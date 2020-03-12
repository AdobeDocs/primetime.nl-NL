---
description: 'null'
seo-description: 'null'
seo-title: Anonieme domeinlogica
title: Anonieme domeinlogica
uuid: bd0e8e51-27dc-4ccf-b285-a80c2ab9e260
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Anonieme domeinlogica{#anonymous-domain-logic}

## Logica voor domeinregistratie {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

De verwijzingsimplementatie past de volgende logica voor anonieme domeinregistratie toe:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. Zoek de domeinnaam in de `DomainServerInfo` tabel op.
1. Als u een item niet kunt vinden, voegt u een item in de tabel in.

   De standaardwaarden zijn:

   * `authentication is not required`
   * `no membership maximum`
   Als de authentificatie voor het gevraagde domein wordt vereist, zorg ervoor dat een geldig authentificatietoken in het verzoek is. Als Auth Namespace in het gegevensbestand wordt gespecificeerd, moet het teken de gespecificeerde Namespace van de Auth aanpassen.
1. Retourfout als verificatie vereist is, maar er geen geldig auteur-token beschikbaar is `DOM_AUTHENTICATION_REQUIRED (503)`.
1. Controleer of het apparaat is geregistreerd bij het domein:

   1. Zoek de domeinnaam in de `DomainMembership` tabel op.
   1. Vergelijk de machine GUID die u van met de machine GUID in het verzoek de plaats bepaalt.
   1. Als dit een nieuwe machine is, voeg een ingang in de `DomainMembership` lijst toe.
   1. Retourfout als het een nieuw apparaat is en de `Max Membership` `DOM_LIMIT_REACHED (502)`waarde is bereikt.

1. Alle domeinsleutels voor dit domein in de `DomainKeys` tabel opzoeken:

   1. Als `DomainServerInfo` erop wijst dat de sleutels moeten worden gerold, produceer een nieuw zeer belangrijk paar.
   1. Sla het sleutelpaar in de `DomainKeys` tabel op met een toetsversie die één getal hoger is dan de hoogste bestaande toets.
   1. De `Key Rollover Required` markering opnieuw instellen in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

## Logica voor deregistratie van domeinen {#section_C968BBFCBFAB4510A903D169F38C9FCE}

De verwijzingsimplementatie past de volgende logica voor anonieme domein de-registratie toe:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. Zoek de gewenste domeinnaam op in de `DomainServerInfo` tabel.
1. Als de authentificatie voor het gevraagde domein wordt vereist, zorg ervoor een geldig authentificatietoken in het verzoek is.

   Het token moet ook overeenkomen met de Auth Namespace die in de database is opgegeven.
1. Zoek omhoog de domeinnaam en machine GUID in de `DomainMembership` lijst.

   Retourfout als u geen overeenkomende vermelding kunt vinden `DEREG_DENIED (401)`.

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit `DomainMembership`en stelt u in `DomainServerInfo`, de `Key Rollover Required` markering in.

Omdat een groot aantal machines zich bij het domein kan aansluiten, kunt u niet eenvoudig machine identiteitskaart aanpassen In plaats daarvan, wordt de willekeurige machine GUID die aan de machine tijdens individualisering wordt toegewezen toegepast.
