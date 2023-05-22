---
title: Anonieme domeinen
description: Anonieme domeinen
copied-description: true
exl-id: a9358582-ad25-4016-94d2-cd82b4c00573
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Anonieme domeinen {#anonymous-domains}

In dit geval, behoren een groot aantal apparaten tot één enkel domein, en de authentificatie kan niet worden vereist. Als u dit type domein wilt gebruiken in de referentie-implementatie, maakt u het beleid waarin wordt opgegeven dat domeinregistratie verplicht is. Geef de URL van de domeinserver op als `https:// host:port/flashaccess/domainserver/domainname/` en geef anonieme verificatie op.

De referentie-implementatie implementeert de volgende logica voor domeinregistratie:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. De domeinnaam opzoeken in het dialoogvenster `DomainServerInfo` tabel. Als een item niet wordt gevonden, voegt u een item in de tabel in (standaardwaarden: verificatie is niet vereist en geen lidmaatschapsmaximum).
1. Als verificatie is vereist voor het gevraagde domein, controleert u of een geldig verificatietoken is opgenomen in de aanvraag en past u de naamruimte Auth aan, indien opgegeven in de database.

   1. Als verificatie is vereist maar geen geldig auteur-token is opgegeven, retourneert u een fout `DOM_AUTHENTICATION_REQUIRED (503)`.

1. Controleer of het apparaat al bij het domein is geregistreerd:

   1. De domeinnaam opzoeken in het dialoogvenster `DomainMembership` tabel. Voor elke gevonden machine GUID, vergelijk met de machine GUID in het verzoek. Als dit een nieuwe computer is, voegt u een item toe aan de `DomainMembership` tabel.

   1. Als het een nieuw apparaat is en Max Lidmaatschap reeds is bereikt, terugkeer fout `DOM_LIMIT_REACHED (502)`.

1. Alle domeinsleutels voor dit domein opzoeken in het dialoogvenster `DomainKeys` tabel.

   1. Indien `DomainServerInfo` geeft aan welke toetsen moeten worden omgedraaid, genereert een nieuw sleutelpaar, slaat dit op in het dialoogvenster `DomainKeys` tabel (met toetsversie één hoger dan de hoogste bestaande toets) en opnieuw instellen `Key Rollover Required` markering in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

De verwijzingsimplementatie voert de volgende logica voor domein uit deïnschrijving:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. Opzoeken van de gevraagde domeinnaam in het dialoogvenster `DomainServerInfo` tabel.
1. Als verificatie is vereist voor het gevraagde domein, controleert u of een geldig verificatietoken is opgenomen in de aanvraag en past u de naamruimte Auth aan, indien opgegeven in de database.
1. Opzoeken van de domeinnaam en machine GUID in het dialoogvenster `DomainMembership` tabel. Als geen overeenkomend item wordt gevonden, retourneert u een fout `DEREG_DENIED (401)`.

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit `DomainMembership` en stelt de `Key Rollover Required` markering in `DomainServerInfo`.

In dit geval, aangezien een groot aantal machines zich bij het domein kon aansluiten, is volledig het aanpassen van machine identiteitskaart niet mogelijk. In plaats daarvan, wordt de willekeurige machine GUID die aan de machine tijdens individualisering wordt toegewezen gebruikt.
