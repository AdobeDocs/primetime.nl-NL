---
title: Anonieme domeinlogica
description: Anonieme domeinlogica
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Anonieme domeinlogica{#anonymous-domain-logic}

## Logica {#section_C91DCD49D7D44570AF98C2D7B8A283F9} voor domeinregistratie

De verwijzingsimplementatie past de volgende logica voor anonieme domeinregistratie toe:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. Zoek de domeinnaam op in de tabel `DomainServerInfo`.
1. Als u een item niet kunt vinden, voegt u een item in de tabel in.

   De standaardwaarden zijn:

   * `authentication is not required`
   * `no membership maximum`

   Als de authentificatie voor het gevraagde domein wordt vereist, zorg ervoor dat een geldig authentificatietoken in het verzoek is. Als Auth Namespace in het gegevensbestand wordt gespecificeerd, moet het teken de gespecificeerde Namespace van de Auth aanpassen.
1. Als verificatie is vereist, maar er geen geldig auteur-token beschikbaar is, retourneert u de fout `DOM_AUTHENTICATION_REQUIRED (503)`.
1. Controleer of het apparaat is geregistreerd bij het domein:

   1. Zoek de domeinnaam op in de tabel `DomainMembership`.
   1. Vergelijk de machine GUID die u met de machine GUID in het verzoek bepaalt.
   1. Als dit een nieuwe machine is, voeg een ingang in `DomainMembership` lijst toe.
   1. Als het een nieuw apparaat is en `Max Membership` waarde is bereikt, terugkeer fout `DOM_LIMIT_REACHED (502)`.

1. Zoek alle domeinsleutels voor dit domein in `DomainKeys` lijst op:

   1. Als `DomainServerInfo` erop wijst dat de sleutels moeten worden omgedraaid, produceer een nieuw zeer belangrijk paar.
   1. Sla het sleutelpaar op in de tabel `DomainKeys`, met een sleutelversie die één getal hoger is dan de hoogste bestaande sleutel.
   1. Stel de markering `Key Rollover Required` in `DomainServerInfo` opnieuw in.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

## Domein deregistration logic {#section_C968BBFCBFAB4510A903D169F38C9FCE}

De verwijzingsimplementatie past de volgende logica voor anonieme domein de-registratie toe:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. Zoek de gewenste domeinnaam op in de tabel `DomainServerInfo`.
1. Als de authentificatie voor het gevraagde domein wordt vereist, zorg ervoor een geldig authentificatietoken in het verzoek is.

   Het token moet ook overeenkomen met de Auth Namespace die in de database is opgegeven.
1. Zoek omhoog de domeinnaam en machine GUID in `DomainMembership` lijst.

   Als u een overeenkomende vermelding niet kunt vinden, retourneert u de fout `DEREG_DENIED (401)`.

1. Als dit geen voorproefverzoek is, schrap de ingang van `DomainMembership`, en in `DomainServerInfo`, plaats de `Key Rollover Required` vlag.

Omdat een groot aantal machines zich bij het domein kan aansluiten, kunt u niet eenvoudig machine identiteitskaart aanpassen In plaats daarvan, wordt de willekeurige machine GUID die aan de machine tijdens individualisering wordt toegewezen toegepast.
