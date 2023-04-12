---
title: MVPD Direct Integration Plan
description: MVPD Direct Integration Plan
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%

---


# MVPD kickstart-handleiding: Directe integratieplan voor MVPD {#mvpd-dir-int-plan}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding {#mvpd-kickstart-intro}

Welkom bij Adobe Primetime-verificatie voor tv overal.  Wij kijken ernaar uit met u samen te werken.

>[!NOTE]
>
>Dit is de Gids van Kickstart voor de Verdelers van de Video van Multikanaal (MVPDs). Als u een programmeur (inhoudsleverancier) bent, zie [Kickstart-handleiding voor programmeurs](/help/authentication/programmer-kickstart-guide.md).

Ondersteuning is altijd beschikbaar via het Primetime-verificatietarensysteem op Zendesk. Hier vindt u ook voorbeelden, documentatie en videozelfstudies voor onze processen. Voor gebruik [Zendesk](https://adobeprimetime.zendesk.com/), moet u zich registreren en een account maken op https://tve.zendesk.com/home. Er is geen limiet voor het aantal gebruikers dat u kunt registreren en die opmerkingen op een ticket kunnen zien of plaatsen. Alle ondersteuningsvragen moeten worden gericht aan: tve-support op adobe.com

**Teamcontactpersonen**:

**Ondersteuning** - Voor alle vragen, incidenten of functieverzoeken **tve-support@adobe.com**.

## 1. Kick-offvergaderingen {#kickoff-meetings}

De mogelijkheden voor deze bijeenkomsten zijn het begin van technische besprekingen tussen Adobe en het MVPD. Op dit moment van het proces moeten beide partijen documenten uitwisselen. Als follow-up moet Adobe een ticket openen in ons kaartverkoopsysteem (https://tve.zendesk.com/) om de status van de integratie te kunnen volgen.

## 2. Functies {#features}

Adobe zal opstelling een wekelijkse statusvraag om het algemene programma, de stappen, de chronologie, en implementatiedetails van de integratie te bespreken en te volgen. In deze fase voert Adobe een evaluatie uit van de specificaties van het MVPD. Het resultaat hiervan moet een speciale pagina zijn die alle functies bevat die de MVPD nodig heeft. Het MVPD zal Adobe een specificatiedocument verzenden, waarin de verificatie-/vergunningsuitvoering van het MVPD wordt gespecificeerd.

Te verduidelijken items, zie [MVPD-integratiefuncties](/help/authentication/mvpd-integr-features.md).

Er zijn verschillende instellingen die op dit punt in detail moeten worden beschreven:

* **URL van MVPD-logo** - Dit is een bestand met de volgende afmetingen: 112 x 33 pixels. Het logo wordt weergegeven door Programmers op hun sites wanneer de gebruiker op de knop Aanmelden klikt om hun Pay TV-provider te selecteren.
* **TTL-waarden (time-to-live)** - De TTL wordt typisch geplaatst door MVPD tijdens het authentificatie/goedkeuringsproces. Nochtans kan Adobe die waarden van TTL met voeten treden en verschillende waarden verstrekken afhankelijk van wat door zowel de Programmer als MVPD wordt overeengekomen.
* **Weergavenaam** - Dit wordt weergegeven door programmeurs op hun sites wanneer de gebruiker op de knop Aanmelden klikt om hun leverancier van betaaltelevisie te selecteren.
* **Referenties testen** - Beide profielen (ophaling en productie) moeten een lijst met testgegevens hebben.

>[!IMPORTANT]
>
>Elke keer dat een gebruiker een machtigingsstroom start, wordt hij gekoppeld aan één ondoorzichtige, unieke gebruikersnaam.  De gebruikers-id wordt gebruikt om de gebruiker van de app van een programmeur te identificeren, maar is afkomstig van de MVPD.

>[!CAUTION]
>
>Een belangrijke kennisgeving voor elke MVPD: De gebruikers-id mag GEEN PII (Persoonlijk identificeerbare informatie) bevatten, informatie die zelfstandig kan worden gebruikt of met andere informatie om de gebruiker te identificeren, in contact te brengen of te vinden.

## 2. Metagegevensuitwisseling {#metadata-ex}

Beide partijen moeten de metagegevens uitwisselen voor alle betrokken omgevingen (productie, staging, enz.).

* **Adobe**
   * Voor het opvoeren van milieu kunnen de Adobe SP meta-gegevens van: worden teruggewonnen [Sp-metagegevens voor verificatieopmaaksjablonen](https://sp.auth-staging.adobe.com/sp/metadata)
   * Voor de productieomgeving kunnen Adobe SP-metagegevens worden opgehaald: [SP-metagegevens voor productie van verificatie](https://sp.auth.adobe.com/sp/metadata)

* **MVPD**
   * Metagegevens (opvoeren/maken) toevoegen.

## 4. IP-lijst toestaan {#allow-ip-list}

De volgende IPs zou in de firewall van MVPD moeten worden gewhitelisteerd. Gelieve te contacteren Adobe voor de lijst van IPs.

* Voor verificatie bij primetime moeten firewalls worden geopend op poorten 80 en 443, zodat toegang tot beperkte bronnen mogelijk is.

* MVPD moet een lijst van IP adressen voor authentificatie en vergunningsservers (als dit het geval is) toevoegen.

## 5. Ontwikkeling {#deve}

De duur van de ontwikkelingsfase wordt bepaald na de herziening van de specificaties en rekening houdend met de punten die beide zijden intekenen. Adobe moet aangepaste code schrijven voor het machtigingsonderdeel.

>[!NOTE]
>
>Merk op dat de vergunning per middel wordt uitgevoerd. De vergunningstransactie wordt typisch uitgevoerd met een koord van identiteitskaart, dat van de plaats van de Programmer wordt overgegaan, die het kanaal vertegenwoordigen waarvoor de gebruiker om toestemming verzoekt. Deze identiteitskaart van Middel wordt gevestigd tussen Programmer en MVPD en kan zo korrelig zijn zoals noodzakelijk.

## 6. Adobe-omgevingen {#adobe-env}

Adobe biedt verschillende omgevingen voor verschillende stadia van het ontwikkelingsproces:

* **Prequalificatie** (PRE-QUAL): De PRE-QUAL-omgeving bevat de volgende releasekandidaat. Adobe integreert aanvankelijk nieuwe partners in dit milieu, alvorens de integratie aan het milieu van de Versie te bevorderen. De partners hebben twee weken om op het PRE-QUAL milieu te testen en moeten uitdrukkelijk om het even welke veranderingen in de PRE-QUAL configuratie verzoeken (contacteer uw vertegenwoordiger van Adobe voor details over het proces van het veranderingsverzoek). Bugfixes brengen nieuwe plaatsingen in dit milieu teweeg.
* **Geen** (RELEASE): Adobe wordt hier geïmplementeerd.

Voor meer informatie over hoe te om de milieu&#39;s van de Adobe te gebruiken, zie [De Adobe-omgevingen begrijpen](/help/authentication/understanding-the-adobe-environments.md)

## 7. Implementatie in fasen {#stag-env}

Gebaseerd op de meta-gegevens die van MVPD worden ontvangen, zal Adobe tot een nieuwe MVPD in het authentificatiesysteem van Primetime leiden en vormen. Dit zal in Adobe prequal het opvoeren milieu worden opgesteld, en zal met onze testprogrammeur (TestDistributors) worden gevormd.

MVPD moet de zelfde plaatsing in hun QA/het opvoeren/testmilieu doen.

## 8. Testen en problemen oplossen {#tes-troubleshoot}

In deze fase, Adobe en de test MVPD en los de integratie problemen op. Het Primetime-verificatieteam kan de API-testsite gebruiken om de integratie te testen. Meer informatie over het gebruik van de API-testsite voor Adobe vindt u op [Verificatie- en autorisatiestromen testen met de testsite Adobe API](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).

Wanneer het testen en het oplossen van problemen met succes heeft voltooid, wordt de integratie toegelaten in Adobe het opvoeren milieu. Op dit punt, kan Adobe MVPD met daadwerkelijke programmeur integreren.

## 9. Implementatie van productie {#prod-dep}

* MVPD moet eerst in het productieprofiel opstellen, om de connectiviteit te testen.

* Adobe wordt ingezet in de productie op voorhand.

* Alle partijen kunnen nu het productieprofiel testen.

* Als alles op dit punt ok is, kan Adobe de integratie naar de milieu van de versieproductie (&quot;levend&quot;) bewegen, die aan alle gebruikers beschikbaar is.

## 10 Doorverwijsprocedures {#esc-proc}

Zodra de integratie in productie levend is is het kritiek om de beste klantenervaring te verstrekken. Om het geval van een server neer kwestie te verzekeren, moet MVPDs escalatieproceduredocumentatie voor kwesties verstrekken die aan Adobe aandacht worden gebracht.

Op zijn beurt levert Adobe MVPD&#39;s het meest recente Primetime-escalatieproces voor verificatie.


<!--- [!RELATEDINFORMATION]
>
>* [Programmer Kickstart Guide](/help/authentication/programmer-kickstart-guide.md)
>* [MVPD Integration Guide](/help/authentication/mvpd-integr-features.md)
-->
