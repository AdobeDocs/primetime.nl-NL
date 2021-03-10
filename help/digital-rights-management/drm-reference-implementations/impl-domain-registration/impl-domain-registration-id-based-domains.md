---
title: Logica voor domeinregistratie op basis van identiteit
description: Logica voor domeinregistratie op basis van identiteit
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Identiteitsgebaseerde logica voor domeinregistratie{#identity-based-domain-registration-logic}

## Logica {#section_149C247458954877AF158B4A09A8526B} voor domeinregistratie

De verwijzingsimplementatie past de volgende logica voor op identiteit-gebaseerde domeinregistratie toe:

1. Bepaal de domeinnaam die aan een aangewezen gebruiker moet worden toegewezen.

   De domeinnaam ( `namequalifier:username`) wordt geëxtraheerd uit het verificatietoken. Als een token niet beschikbaar is, wordt een fout gegenereerd.
1. Zoek de domeinnaam op in de tabel `DomainServerInfo`.

   Als er geen item wordt gevonden, voegt u een item in. De standaardwaarden zijn:

   * `authentication required`
   * `max domain membership=5`

   .

1. Om te verifiëren dat het apparaat met het domein is geregistreerd:

   1. Zoek de `domainname` in de `UserDomainMembership` lijst op:

      1. Vergelijk de id voor elke machine-id die zich bevindt met de machine-id in de aanvraag.
      1. Als dit een nieuwe machine is, voeg een ingang aan `UserDomainMembership` lijst toe.
      1. Zoek naar de passende verslagen in `UserDomainRefCount` lijst.
      1. Als een ingang niet voor deze machine GUID bestaat, voeg een verslag toe.
   1. Retourfout als het een nieuw apparaat is en de waarde `Max Membership` is bereikt.


1. Zoek alle domeinsleutels voor dit domein in `DomainKeys` lijst op:

   1. Als `DomainServerInfo` erop wijst dat de sleutels moeten worden omgedraaid, een nieuw zeer belangrijk paar produceren,
   1. Sla het paar op in de tabel `DomainKeys`, met een toetsversie die hoger is dan de hoogste bestaande toets.
   1. Stel de markering `Key Rollover Required` in `DomainServerInfo` opnieuw in.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

## Domein deregistration logic {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

De verwijzingsimplementatie past de volgende logica voor op identiteit-gebaseerde domein toe deïnregistration:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen.

   De domeinnaam is `namequalifier:username`, die uit het authentificatietoken wordt gehaald. Als er geen token beschikbaar is, treedt een retourfout `DOM_AUTHENTICATION_REQUIRED (503)` op.
1. Zoek de gewenste domeinnaam op in de tabel `DomainServerInfo`.
1. Zoek de domeinnaam op in de tabel `UserDomainMembership`.
1. Vergelijk elke machine-id die u vindt met de machine-id in de aanvraag.
1. Zoek het corresponderende item in de tabel `UserDomainRefCount`.

   Retourfout wanneer geen overeenkomend item wordt gevonden.

1. Als dit geen voorproefverzoek is, schrap de ingang van `UserDomainRefCount` lijst.
1. Als er geen extra ingangen in die lijst voor de machine zijn, schrap de ingang van `UserDomainMembership` en plaats de [!DNL Key Rollover Required] vlag in `DomainServerInfo` bezit.

Elke gebruiker kan een klein aantal machines registreren, zodat kunt u volledige machine identiteitskaart en `matches()` methode gebruiken om machines te tellen. Omdat een gebruiker meerdere keren kan registreren, via meerdere AIR-toepassingen of Players in verschillende browsers, moet de server een aantal verwijzingen bijhouden zodat deregistratie ook kan worden geteld.

>[!NOTE]
>
>De-registratie is niet voltooid totdat alle domeintokens op de computer zijn ingeleverd.

