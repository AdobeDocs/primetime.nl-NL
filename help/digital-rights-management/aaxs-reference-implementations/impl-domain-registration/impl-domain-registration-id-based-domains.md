---
seo-title: Identiteitsgebaseerde domeinen
title: Identiteitsgebaseerde domeinen
uuid: 34cad19b-1adb-4e0c-ac59-50632f6988f7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Identiteitsgebaseerde domeinen {#identity-based-domains}

In dit gebruiksgeval, heeft elke voor authentiek verklaarde gebruiker zijn eigen domein, en een bepaald aantal apparaten wordt toegestaan om zich bij het domein aan te sluiten. Als u dit type domein wilt gebruiken in de referentie-implementatie, maakt u een beleid waarin domeinregistratie wordt opgegeven. Geef de host en poort van uw server op voor de URL van de domeinserver en geef op dat verificatie van gebruikersnaam en wachtwoord vereist is.

De referentie-implementatie implementeert de volgende logica voor domeinregistratie:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen. De domeinnaam wordt * `namequalifier:username`* uit het verificatietoken geëxtraheerd. Als er geen verificatietoken is, retourneert u de fout DOM_AUTHENTICATION_REQUIRED (503).
1. De domeinnaam opzoeken in de `DomainServerInfo` tabel. Als een ingang niet wordt gevonden, neem een ingang in de lijst op (de standaardwaarden worden vereiste authentificatie, maximum domeinlidmaatschap=5).
1. Controleer of het apparaat al bij het domein is geregistreerd:

   1. Zoek de domeinnaam op in de `UserDomainMembership` tabel. Vergelijk voor elke gevonden machine-id de machine-id in de aanvraag. Als dit een nieuwe machine is, voeg een ingang aan de `UserDomainMembership` lijst toe. Zoek vervolgens de overeenkomende records in de `UserDomainRefCount` tabel. Als een ingang niet voor deze machine GUID bestaat, voeg een verslag toe.

   1. Als dit een nieuw apparaat is en Max Membership al is bereikt, retourneert u de fout DOM_LIMIT_REACHED (502).

1. Alle domeinsleutels voor dit domein opzoeken in de tabel DomainKeys.

   1. Als `DomainServerInfo` aangeeft dat de toetsen moeten worden omgedraaid, genereert u een nieuw sleutelpaar, slaat u dit op in de `DomainKeys` tabel (met een toetsversie die hoger is dan de hoogste bestaande sleutel) en stelt u de markering &#39;Key Rollover vereist&#39; in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

De verwijzingsimplementatie, voert de volgende logica voor domein uit deregistratie:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen. De domeinnaam wordt *namequalifier:gebruikersnaam* geëxtraheerd uit het verificatietoken. Als er geen verificatietoken is, retourneert u de fout DOM_AUTHENTICATION_REQUIRED (503).
1. Opzoeken van de gewenste domeinnaam in de `DomainServerInfo` tabel.
1. De domeinnaam opzoeken in de `UserDomainMembership` tabel. Vergelijk voor elke gevonden machine-id de machine-id in de aanvraag. Zoek het overeenkomstige item in de `UserDomainRefCount` tabel. Als geen overeenkomend item wordt gevonden, retourneert u de fout DEREG_DENIED (401).

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit de `UserDomainRefCount` tabel. Als die tabel geen items meer bevat voor de computer, verwijdert u het item uit `UserDomainMembership` en stelt u de markering &quot;Rollover vereist&quot; in `DomainServerInfo`.

In dit geval mag elke gebruiker een klein aantal machines registreren, zodat we de volledige machine-id en de `matches()` methode kunnen gebruiken om machines nauwkeurig te tellen. Aangezien de gebruiker zich echter meerdere keren op deze computer kon registreren (via meerdere AIR-toepassingen of Players in verschillende browsers), moet de server ook een referentietelling bijhouden, zodat de deregistratie op de juiste wijze kan worden geteld. De deregistratie kan niet als volledig worden beschouwd, tot alle domeintokens op de computer worden teruggegeven.
