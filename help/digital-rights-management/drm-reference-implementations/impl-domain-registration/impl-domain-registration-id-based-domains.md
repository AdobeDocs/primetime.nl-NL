---
description: 'null'
seo-description: 'null'
seo-title: Logica voor domeinregistratie op basis van identiteit
title: Logica voor domeinregistratie op basis van identiteit
uuid: bc13f7c2-9a20-4f80-b96f-05f7a0fcc343
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Logica voor domeinregistratie op basis van identiteit{#identity-based-domain-registration-logic}

## Logica voor domeinregistratie {#section_149C247458954877AF158B4A09A8526B}

De verwijzingsimplementatie past de volgende logica voor op identiteit-gebaseerde domeinregistratie toe:

1. Bepaal de domeinnaam die aan een aangewezen gebruiker moet worden toegewezen.

   De domeinnaam ( `namequalifier:username`) wordt geëxtraheerd uit het verificatietoken. Als een token niet beschikbaar is, wordt een fout gegenereerd.
1. Zoek de domeinnaam in de `DomainServerInfo` tabel op.

   Als er geen item wordt gevonden, voegt u een item in. De standaardwaarden zijn:

   * `authentication required`
   * `max domain membership=5`
   .

1. Om te verifiëren dat het apparaat met het domein is geregistreerd:

   1. Opzoeken in de `domainname` `UserDomainMembership` tabel:

      1. Vergelijk de id voor elke machine-id die zich bevindt met de machine-id in de aanvraag.
      1. Als dit een nieuwe machine is, voeg een ingang aan de `UserDomainMembership` lijst toe.
      1. Zoek naar de overeenkomstige verslagen in `UserDomainRefCount` lijst.
      1. Als een ingang niet voor deze machine GUID bestaat, voeg een verslag toe.
   1. Retourfout als het een nieuw apparaat is en de `Max Membership` waarde is bereikt.


1. Alle domeinsleutels voor dit domein in de `DomainKeys` tabel opzoeken:

   1. Als `DomainServerInfo` erop wijst dat de sleutels moeten worden gerold, produceer een nieuw zeer belangrijk paar,
   1. Sla het paar in de `DomainKeys` tabel op met een toetsversie die hoger is dan de hoogste bestaande toets.
   1. De `Key Rollover Required` markering opnieuw instellen in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

## Logica voor deregistratie van domeinen {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

De verwijzingsimplementatie past de volgende logica voor op identiteit-gebaseerde domein toe deïnregistration:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen.

   De domeinnaam is `namequalifier:username`, die uit het authentificatietoken wordt gehaald. Als er geen token beschikbaar is, treedt een geretourneerde fout `DOM_AUTHENTICATION_REQUIRED (503)` op.
1. Zoek de gewenste domeinnaam op in de `DomainServerInfo` tabel.
1. Zoek de domeinnaam in de `UserDomainMembership` tabel op.
1. Vergelijk elke machine-id die u vindt met de machine-id in de aanvraag.
1. Zoek het corresponderende item in de `UserDomainRefCount` tabel.

   Retourfout wanneer geen overeenkomend item wordt gevonden.

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit de `UserDomainRefCount` tabel.
1. Als er geen extra items in die tabel staan voor het systeem, verwijdert u het item uit `UserDomainMembership` en stelt u de [!DNL Key Rollover Required] markering in de `DomainServerInfo` eigenschap in.

Elke gebruiker kan een klein aantal machines registreren, zodat kunt u volledige machine identiteitskaart en de methode gebruiken om machines te tellen. `matches()` Omdat een gebruiker meerdere keren kan registreren, via meerdere AIR-toepassingen of Players in verschillende browsers, moet de server een referentietelling bijhouden zodat de-registratie ook kan worden geteld.

>[!NOTE]
>
>De-registratie is niet voltooid totdat alle domeintokens op de computer zijn ingeleverd.

