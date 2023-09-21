---
title: Identiteitsgebaseerde domeinen
description: Identiteitsgebaseerde domeinen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Identiteitsgebaseerde domeinen {#identity-based-domains}

In dit gebruiksgeval, heeft elke voor authentiek verklaarde gebruiker zijn eigen domein, en een bepaald aantal apparaten wordt toegestaan om zich bij het domein aan te sluiten. Als u dit type domein wilt gebruiken in de referentie-implementatie, maakt u een beleid waarin domeinregistratie wordt opgegeven. Geef de host en poort van uw server op voor de URL van de domeinserver en geef op dat verificatie van gebruikersnaam en wachtwoord vereist is.

De referentie-implementatie implementeert de volgende logica voor domeinregistratie:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen. De domeinnaam is * `namequalifier:username`* uit het verificatietoken gehaald. Als er geen verificatietoken is, retourneert u de fout DOM_AUTHENTICATION_REQUIRED (503).
1. De domeinnaam opzoeken in het dialoogvenster `DomainServerInfo` tabel. Als een ingang niet wordt gevonden, neem een ingang in de lijst op (de standaardwaarden worden vereiste authentificatie, maximum domeinlidmaatschap=5).
1. Controleer of het apparaat al bij het domein is geregistreerd:

   1. De domeinnaam opzoeken in het dialoogvenster `UserDomainMembership` tabel. Vergelijk voor elke gevonden machine-id de machine-id in de aanvraag. Als dit een nieuwe computer is, voegt u een item toe aan de `UserDomainMembership` tabel. Zoek vervolgens de overeenkomende records in `UserDomainRefCount` tabel. Als een ingang niet voor deze machine GUID bestaat, voeg een verslag toe.

   1. Als dit een nieuw apparaat is en Max Membership al is bereikt, retourneert u de fout DOM_LIMIT_REACHED (502).

1. Alle domeinsleutels voor dit domein opzoeken in de tabel DomainKeys.

   1. Indien `DomainServerInfo` geeft aan dat de toetsen moeten worden omgedraaid, een nieuw sleutelpaar moeten genereren en opgeslagen in het dialoogvenster `DomainKeys` tabel (met toetsversie één hoger dan de hoogste bestaande toets) en stel de markering &quot;Key Rollover vereist&quot; in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

De verwijzingsimplementatie, voert de volgende logica voor domein uit deregistratie:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen. De domeinnaam wordt *namequalifier:gebruikersnaam* uit het verificatietoken gehaald. Als er geen verificatietoken is, retourneert u de fout DOM_AUTHENTICATION_REQUIRED (503).
1. Opzoeken van de gevraagde domeinnaam in het dialoogvenster `DomainServerInfo` tabel.
1. De domeinnaam opzoeken in het dialoogvenster `UserDomainMembership` tabel. Vergelijk voor elke gevonden machine-id de machine-id in de aanvraag. De bijbehorende vermelding zoeken in het dialoogvenster `UserDomainRefCount` tabel. Als geen overeenkomend item wordt gevonden, retourneert u de fout DEREG_DENIED (401).

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit `UserDomainRefCount` tabel. Als de tabel geen items meer bevat voor het systeem, verwijdert u het item uit `UserDomainMembership` en stelt de markering &quot;Key Rollover Required&quot; in `DomainServerInfo`.

In dit geval mag elke gebruiker een klein aantal machines registreren, zodat de volledige machine-id en de `matches()` methode om machines nauwkeurig te tellen. Aangezien de gebruiker zich echter meerdere keren op deze computer kon registreren (via meerdere AIR-toepassingen of Players in verschillende browsers), moet de server ook een referentietelling bijhouden, zodat de deregistratie op de juiste wijze kan worden geteld. De deregistratie kan niet als volledig worden beschouwd, tot alle domeintokens op de computer worden teruggegeven.
