---
title: Logica voor domeinregistratie op basis van identiteit
description: Logica voor domeinregistratie op basis van identiteit
copied-description: true
exl-id: 6e391fce-00b4-45cf-b785-3b0ec734a11e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Logica voor domeinregistratie op basis van identiteit{#identity-based-domain-registration-logic}

## Logica voor domeinregistratie {#section_149C247458954877AF158B4A09A8526B}

De verwijzingsimplementatie past de volgende logica voor op identiteit-gebaseerde domeinregistratie toe:

1. Bepaal de domeinnaam die aan een aangewezen gebruiker moet worden toegewezen.

   De domeinnaam ( `namequalifier:username`) wordt uit het verificatietoken geëxtraheerd. Als een token niet beschikbaar is, wordt een fout gegenereerd.
1. De domeinnaam opzoeken in het dialoogvenster `DomainServerInfo` tabel.

   Als er geen item wordt gevonden, voegt u een item in. De standaardwaarden zijn:

   * `authentication required`
   * `max domain membership=5`

   .

1. Om te verifiëren dat het apparaat met het domein is geregistreerd:

   1. Zoek de `domainname` in de `UserDomainMembership` tabel:

      1. Vergelijk de id voor elke machine-id die zich bevindt met de machine-id in de aanvraag.
      1. Als dit een nieuwe computer is, voegt u een item toe aan de `UserDomainMembership` tabel.
      1. Zoeken naar de bijbehorende records in `UserDomainRefCount` tabel.
      1. Als een ingang niet voor deze machine GUID bestaat, voeg een verslag toe.
   1. Als het een nieuw apparaat is, en `Max Membership` waarde is bereikt, retourfout.


1. Alle domeinsleutels voor dit domein opzoeken in het dialoogvenster `DomainKeys` tabel:

   1. Indien `DomainServerInfo` geeft aan dat de toetsen moeten worden omgedraaid, een nieuw sleutelpaar genereren;
   1. Sla het paar op in het dialoogvenster `DomainKeys` met een hoofdversie die hoger is dan de hoogste bestaande toets.
   1. De `Key Rollover Required` markering in `DomainServerInfo`.

   1. Voor elke domeinsleutel genereert u een domeinreferentie.

## Logica voor deregistratie van domeinen {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

De verwijzingsimplementatie past de volgende logica voor op identiteit-gebaseerde domein toe deïnregistration:

1. Bepaal de domeinnaam die aan deze gebruiker moet worden toegewezen.

   De domeinnaam is `namequalifier:username`, die wordt geëxtraheerd uit het verificatietoken. Retourfout als er geen token beschikbaar is `DOM_AUTHENTICATION_REQUIRED (503)` voorkomt.
1. Opzoeken in het dialoogvenster `DomainServerInfo` tabel.
1. De domeinnaam opzoeken in het dialoogvenster `UserDomainMembership` tabel.
1. Vergelijk elke machine-id die u vindt met de machine-id in de aanvraag.
1. Zoek de bijbehorende vermelding in het dialoogvenster `UserDomainRefCount` tabel.

   Retourfout wanneer geen overeenkomend item wordt gevonden.

1. Als dit geen voorvertoningsverzoek is, verwijdert u het item uit het dialoogvenster `UserDomainRefCount` tabel.
1. Als die tabel geen extra items bevat voor de computer, verwijdert u het item uit `UserDomainMembership` en stelt de [!DNL Key Rollover Required] vlag in de `DomainServerInfo` eigenschap.

Elke gebruiker kan een klein aantal computers registreren, zodat u de volledige machine-id en de `matches()` methode om machines te tellen. Omdat een gebruiker meerdere keren kan registreren, via meerdere AIR-toepassingen of Players in verschillende browsers, moet de server een referentietelling bijhouden zodat de-registratie ook kan worden geteld.

>[!NOTE]
>
>De-registratie is niet voltooid totdat alle domeintokens op de computer zijn ingeleverd.
