---
title: MVPD Direct Integration Plan
description: MVPD Direct Integration Plan
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%

---

# MVPD kickstart guide: MVPD Direct Integration Plan {#mvpd-dir-int-plan}

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

De mogelijkheid voor deze bijeenkomsten is het begin van technische besprekingen tussen Adobe en de MVPD. Op dit moment van het proces moeten beide partijen documenten uitwisselen. Als follow-up moet de Adobe een ticket openen in ons kaartverkoopsysteem (https://tve.zendesk.com/) om de status van de integratie te kunnen volgen.

## 2. Functies {#features}

De Adobe zal een wekelijkse statusvraag opstellen om het algemene programma, de stappen, de chronologie, en de implementatiedetails van de integratie te bespreken en te volgen. In deze fase voert de Adobe een herziening uit van de specificaties van het MVPD. Het resultaat hiervan moet een speciale pagina zijn die alle functies bevat die de MVPD nodig heeft. De MVPD zal de Adobe een specificatiedocument sturen met gedetailleerde informatie over de uitvoering van de verificatie/machtiging van de MVPD.

Te verduidelijken items, zie [MVPD-integratiefuncties](/help/authentication/mvpd-integr-features.md).

Er zijn verschillende instellingen die op dit punt in detail moeten worden beschreven:

* **URL van MVPD-logo** - Dit bestand heeft de volgende afmetingen: 112 x 33 pixels. Het logo wordt weergegeven door Programmers op hun sites wanneer de gebruiker op de knop Aanmelden klikt om hun Pay TV-provider te selecteren.
* **TTL-waarden (time-to-live)** - De TTL wordt typisch geplaatst door MVPD tijdens het authentificatie/goedkeuringsproces. Nochtans kan de Adobe die waarden van TTL met voeten treden en verschillende waarden verstrekken afhankelijk van wat door zowel de Programmer als MVPD wordt overeengekomen.
* **Weergavenaam** - Dit wordt weergegeven door programmeurs op hun sites wanneer de gebruiker op de knop Aanmelden klikt om hun leverancier van betaaltelevisie te selecteren.
* **Referenties testen** - Beide profielen (ophaling en productie) moeten een lijst met testgegevens hebben.

>[!IMPORTANT]
>
>Elke keer dat een gebruiker een machtigingsstroom start, wordt hij gekoppeld aan één ondoorzichtige, unieke gebruikersnaam.  De gebruikers-id wordt gebruikt om de gebruiker van de app van een programmeur te identificeren, maar is afkomstig van de MVPD.

>[!CAUTION]
>
>Een belangrijke kennisgeving voor elke MVPD: de gebruikers-id mag GEEN PII (Persoonlijk Identificeerbare Informatie) bevatten, informatie die zelfstandig of met andere informatie kan worden gebruikt om de gebruiker te identificeren, te contacteren of te vinden.

## 2. Metagegevensuitwisseling {#metadata-ex}

Beide partijen moeten de metagegevens uitwisselen voor alle betrokken omgevingen (productie, staging, enz.).

* **Adobe**
   * Voor de testomgeving kunnen de SP-metagegevens van de Adobe worden opgehaald uit: [Sp-metagegevens voor verificatieopmaaksjablonen](https://sp.auth-staging.adobe.com/sp/metadata)
   * Voor de productieomgeving kunnen de SP-metagegevens van de Adobe worden opgehaald uit: [SP-metagegevens voor productie van verificatie](https://sp.auth.adobe.com/sp/metadata)

* **MVPD**
   * Metagegevens (opvoeren/maken) toevoegen.

## 4. IP-lijst toestaan {#allow-ip-list}

De volgende IPs zou in de firewall van MVPD moeten worden gewhitelisteerd. Gelieve te contacteren Adobe voor de lijst van IPs.

* Voor verificatie bij primetime moeten firewalls worden geopend op poorten 80 en 443, zodat toegang tot beperkte bronnen mogelijk is.

* MVPD moet een lijst van IP adressen voor authentificatie en vergunningsservers (als dit het geval is) toevoegen.

## 5. Ontwikkeling {#deve}

De duur van de ontwikkelingsfase wordt bepaald na de herziening van de specificaties en rekening houdend met de punten die beide zijden intekenen. Adobe moet aangepaste code voor het machtigingsonderdeel schrijven.

>[!NOTE]
>
>Merk op dat de vergunning per middel wordt uitgevoerd. De vergunningstransactie wordt typisch uitgevoerd met een koord van identiteitskaart, dat van de plaats van de Programmer wordt overgegaan, die het kanaal vertegenwoordigen waarvoor de gebruiker om toestemming verzoekt. Deze identiteitskaart van Middel wordt gevestigd tussen Programmer en MVPD en kan zo korrelig zijn zoals noodzakelijk.

## 6. Adobe {#adobe-env}

Adobe biedt verschillende omgevingen voor verschillende stadia van het ontwikkelingsproces:

* **Prequalificatie** (PRE-QUAL): De PRE-QUAL-omgeving bevat de volgende releasekandidaat. De Adobe integreert aanvankelijk nieuwe partners in dit milieu, alvorens de integratie aan het milieu van de Versie te bevorderen. De partners hebben twee weken om op het PRE-QUAL milieu te testen en moeten uitdrukkelijk om het even welke veranderingen in de PRE-QUAL configuratie verzoeken (contacteer uw vertegenwoordiger van de Adobe voor details over het proces van het veranderingsverzoek). Bugfixes brengen nieuwe plaatsingen in dit milieu teweeg.
* **Geen** (RELEASE): de huidige productiestructuur van Adobe wordt hier geïmplementeerd in een live omgeving.

Voor meer informatie over het gebruik van de omgevingen van de Adobe raadpleegt u [De Adobe omgevingen begrijpen](/help/authentication/understanding-the-adobe-environments.md)

## 7. Stationering {#stag-env}

Gebaseerd op de meta-gegevens die van MVPD worden ontvangen, zal de Adobe tot een nieuwe MVPD in het authentificatiesysteem van Primetime leiden en vormen. Dit zal in het prequal het opvoeren milieu van de Adobe worden opgesteld, en zal met onze testprogrammeur (TestDistributors) worden gevormd.

MVPD moet de zelfde plaatsing in hun QA/het opvoeren/testmilieu doen.

## 8. Testen en problemen oplossen {#tes-troubleshoot}

In deze fase, Adobe en de test MVPD en los de integratie problemen op. Het Primetime-verificatieteam kan de API-testsite van de Adobe gebruiken om de integratie te testen. Meer informatie over het gebruik van de API-testsite van de Adobe vindt u op [Verificatie- en autorisatiestromen testen met de testsite voor de Adobe-API](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).

Wanneer het testen en het oplossen van problemen met succes heeft voltooid, wordt de integratie toegelaten in de het opvoeren van de versie van de Adobe milieu. Op dit punt, kan de Adobe MVPD met daadwerkelijke programmeur integreren.

## 9. Productie {#prod-dep}

* MVPD moet eerst in het productieprofiel opstellen, om de connectiviteit te testen.

* Adobe wordt ingezet in productie op voorhand.

* Alle partijen kunnen nu het productieprofiel testen.

* Als alles op dit punt goed is, kan de Adobe de integratie naar de milieu van de versieproductie (&quot;levend&quot;) verplaatsen, die aan alle gebruikers beschikbaar is.

## 10. Doorverwijsprocedures {#esc-proc}

Zodra de integratie in productie levend is is het kritiek om de beste klantenervaring te verstrekken. Om de beste reactie in het geval van een server neer kwestie te verzekeren, moeten MVPDs de documentatie van de escalatieprocedure voor kwesties verstrekken die aan de aandacht van de Adobe worden gebracht.

Omgekeerd levert de Adobe MVPDs van het huidigste proces van de authentificatieescalatie Primetime.


<!--- [!RELATEDINFORMATION]
>
>* [Programmer Kickstart Guide](/help/authentication/programmer-kickstart-guide.md)
>* [MVPD Integration Guide](/help/authentication/mvpd-integr-features.md)
-->