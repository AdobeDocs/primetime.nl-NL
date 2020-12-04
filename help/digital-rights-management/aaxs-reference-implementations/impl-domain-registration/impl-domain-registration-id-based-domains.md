---
seo-title: Identiteitsgebaseerde domeinen
title: Identiteitsgebaseerde domeinen
uuid: 34cad19b-1adb-4e0c-ac59-50632f6988f7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# Identiteitsgebaseerde domeinen {#identity-based-domains}

In dit gebruiksgeval, heeft elke voor authentiek verklaarde gebruiker zijn eigen domein, en een bepaald aantal apparaten wordt toegestaan om zich bij het domein aan te sluiten. Als u dit type domein wilt gebruiken in de referentie-implementatie, maakt u een beleid waarin domeinregistratie wordt opgegeven. Geef de host en poort van uw server op voor de URL van de domeinserver en geef op dat verificatie van gebruikersnaam en wachtwoord vereist is.

De referentie-implementatie implementeert de volgende logica voor domeinregistratie:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen. De domeinnaam wordt * `namequalifier:username`* uit het verificatietoken geëxtraheerd. Als er geen verificatietoken is, retourneert u de fout DOM_AUTHENTICATION_REQUIRED (503).
1. De domeinnaam opzoeken in de tabel `DomainServerInfo`. Als een ingang niet wordt gevonden, neem een ingang in de lijst op (de standaardwaarden worden vereiste authentificatie, maximum domeinlidmaatschap=5).
1. Controleer of het apparaat al bij het domein is geregistreerd:

   1. Lookup the domain name in the `UserDomainMembership` table. Vergelijk voor elke gevonden machine-id de machine-id in de aanvraag. Als dit een nieuwe machine is, voeg een ingang aan `UserDomainMembership` lijst toe. Zoek vervolgens de overeenkomende records in de tabel `UserDomainRefCount`. Als een ingang niet voor deze machine GUID bestaat, voeg een verslag toe.

   1. Als dit een nieuw apparaat is en Max Membership al is bereikt, retourneert u de fout DOM_LIMIT_REACHED (502).

1. Alle domeinsleutels voor dit domein opzoeken in de tabel DomainKeys.

   1. Als `DomainServerInfo` erop wijst dat de sleutels over moeten worden gerold, een nieuw zeer belangrijk paar produceren, sparen het in `DomainKeys` lijst (met zeer belangrijke versie één hoger dan de hoogste bestaande sleutel), en terugstellen de &quot;Zeer belangrijke Vereiste vlag van het Rollover in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

De verwijzingsimplementatie, voert de volgende logica voor domein uit deregistratie:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen. De domeinnaam zal *namequalifier:username* uit het authentificatietoken worden gehaald. Als er geen verificatietoken is, retourneert u de fout DOM_AUTHENTICATION_REQUIRED (503).
1. Opzoeken van de gevraagde domeinnaam in de tabel `DomainServerInfo`.
1. De domeinnaam opzoeken in de tabel `UserDomainMembership`. Vergelijk voor elke gevonden machine-id de machine-id in de aanvraag. Zoek het overeenkomstige item in de tabel `UserDomainRefCount`. Als geen overeenkomend item wordt gevonden, retourneert u de fout DEREG_DENIED (401).

1. Als dit geen voorproefverzoek is, schrap de ingang van `UserDomainRefCount` lijst. Als die tabel geen items meer bevat voor de computer, verwijdert u het item uit `UserDomainMembership` en stelt u de markering &quot;Key Rollover Required&quot; in `DomainServerInfo` in.

In dit geval mag elke gebruiker een klein aantal machines registreren, zodat we de volledige machine-id en de `matches()`-methode kunnen gebruiken om machines nauwkeurig te tellen. Aangezien de gebruiker zich echter meerdere keren op deze computer kon registreren (via meerdere AIR-toepassingen of Players in verschillende browsers), moet de server ook een referentietelling bijhouden, zodat de deregistratie op de juiste wijze kan worden geteld. De deregistratie kan niet als volledig worden beschouwd, tot alle domeintokens op de computer worden teruggegeven.
