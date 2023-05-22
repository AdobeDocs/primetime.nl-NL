---
title: Anonieme domeinlogica
description: Anonieme domeinlogica
copied-description: true
exl-id: 4a6c3485-cde7-403f-89d8-f6420df3539a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Anonieme domeinlogica{#anonymous-domain-logic}

## Logica voor domeinregistratie {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

De verwijzingsimplementatie past de volgende logica voor anonieme domeinregistratie toe:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. De domeinnaam opzoeken in het dialoogvenster `DomainServerInfo` tabel.
1. Als u een item niet kunt vinden, voegt u een item in de tabel in.

   De standaardwaarden zijn:

   * `authentication is not required`
   * `no membership maximum`

   Als de authentificatie voor het gevraagde domein wordt vereist, zorg ervoor dat een geldig authentificatietoken in het verzoek is. Als Auth Namespace in het gegevensbestand wordt gespecificeerd, moet het teken de gespecificeerde Namespace van de Auth aanpassen.
1. Retourfout als verificatie vereist is maar geen geldig auteur-token beschikbaar is `DOM_AUTHENTICATION_REQUIRED (503)`.
1. Controleer of het apparaat is geregistreerd bij het domein:

   1. De domeinnaam opzoeken in het dialoogvenster `DomainMembership` tabel.
   1. Vergelijk de machine GUID die u van met de machine GUID in het verzoek de plaats bepaalt.
   1. Als dit een nieuwe computer is, voegt u een item toe aan het dialoogvenster `DomainMembership` tabel.
   1. Als het een nieuw apparaat is en `Max Membership` waarde is bereikt, retourfout `DOM_LIMIT_REACHED (502)`.

1. Alle domeinsleutels voor dit domein opzoeken in het dialoogvenster `DomainKeys` tabel:

   1. Indien `DomainServerInfo` Hiermee geeft u aan dat de toetsen moeten worden omgedraaid en dat er een nieuw sleutelpaar moet worden gegenereerd.
   1. Sla het sleutelpaar op in het dialoogvenster `DomainKeys` met een sleutelversie die één aantal hoger is dan de hoogste bestaande sleutel.
   1. De `Key Rollover Required` markering in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

## Logica voor deregistratie van domeinen {#section_C968BBFCBFAB4510A903D169F38C9FCE}

De verwijzingsimplementatie past de volgende logica voor anonieme domein de-registratie toe:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. Opzoeken in het dialoogvenster `DomainServerInfo` tabel.
1. Als de authentificatie voor het gevraagde domein wordt vereist, zorg ervoor een geldig authentificatietoken in het verzoek is.

   Het token moet ook overeenkomen met de Auth Namespace die in de database is opgegeven.
1. Zoek omhoog de domeinnaam en machine GUID in `DomainMembership` tabel.

   Als u een overeenkomende vermelding niet kunt vinden, retourneert u een fout `DEREG_DENIED (401)`.

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit `DomainMembership`, en in `DomainServerInfo`stelt u de `Key Rollover Required` markering.

Omdat een groot aantal machines zich bij het domein kan aansluiten, kunt u niet eenvoudig machine identiteitskaart aanpassen In plaats daarvan, wordt de willekeurige machine GUID die aan de machine tijdens individualisering wordt toegewezen toegepast.
