---
seo-title: Anonieme domeinen
title: Anonieme domeinen
uuid: ee29ae4d-65b2-48de-b441-18c8cf55de32
translation-type: tm+mt
source-git-commit: 4f196bbd079edeb1a423afee6b4b7e249d380f40
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Anonieme domeinen {#anonymous-domains}

In dit geval, behoren een groot aantal apparaten tot één enkel domein, en de authentificatie kan niet worden vereist. Als u dit type domein wilt gebruiken in de referentie-implementatie, maakt u het beleid waarin u opgeeft dat domeinregistratie verplicht is. Geef de URL van de domeinserver op als `https:// host:port/flashaccess/domainserver/domainname/` en geef anonieme verificatie op.

De referentie-implementatie implementeert de volgende logica voor domeinregistratie:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. De domeinnaam opzoeken in de `DomainServerInfo` tabel. Als een item niet wordt gevonden, voegt u een item in de tabel in (standaardwaarden: verificatie is niet vereist en geen lidmaatschapsmaximum).
1. Als verificatie is vereist voor het gevraagde domein, controleert u of een geldig verificatietoken is opgenomen in de aanvraag en past u de naamruimte Auth aan, indien opgegeven in de database.

   1. Retourfout als verificatie vereist is maar geen geldig autetoken is opgegeven `DOM_AUTHENTICATION_REQUIRED (503)`.

1. Controleer of het apparaat al bij het domein is geregistreerd:

   1. De domeinnaam opzoeken in de `DomainMembership` tabel. Voor elke gevonden machine GUID, vergelijk met de machine GUID in het verzoek. Als dit een nieuwe machine is, voeg een ingang aan de `DomainMembership` lijst toe.

   1. Als het een nieuw apparaat is en Max Lidmaatschap reeds is bereikt, terugkeer fout `DOM_LIMIT_REACHED (502)`.

1. Alle domeinsleutels voor dit domein in de `DomainKeys` tabel opzoeken.

   1. Als `DomainServerInfo` aangeeft dat de toetsen moeten worden omgedraaid, genereert u een nieuw sleutelpaar, slaat u dit op in de `DomainKeys` tabel (met de toetsversie één hoger dan de hoogste bestaande toets) en herstelt u de `Key Rollover Required` markering in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

De verwijzingsimplementatie voert de volgende logica voor domein uit deïnschrijving:

1. Analyseer de domeinnaam van de aanvraag-URL.
1. Opzoeken van de gewenste domeinnaam in de `DomainServerInfo` tabel.
1. Als verificatie is vereist voor het gevraagde domein, controleert u of een geldig verificatietoken is opgenomen in de aanvraag en past u de naamruimte Auth aan, indien opgegeven in de database.
1. Zoek de domeinnaam en machine GUID in de `DomainMembership` lijst op. Retourfout als geen overeenkomend item wordt gevonden `DEREG_DENIED (401)`.

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit `DomainMembership` en stelt u de `Key Rollover Required` markering in `DomainServerInfo`.

In dit geval, aangezien een groot aantal machines zich bij het domein kon aansluiten, is volledig het aanpassen van machine identiteitskaart niet mogelijk. In plaats daarvan, wordt de willekeurige machine GUID die aan de machine tijdens individualisering wordt toegewezen gebruikt.
