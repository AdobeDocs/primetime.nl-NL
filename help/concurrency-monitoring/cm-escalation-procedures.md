---
title: Toezicht op de valutamarkt
description: Toezicht op de valutamarkt
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# Toezicht op de valutamarkt {#esc-procedures}

>[!NOTE]
>
>Bel de hotline: +1-205-693-9813 en stuur een e-mail naar `tve-support@adobe.com` opnemen van &quot;URGENT - INCIDENT&quot; in de onderwerpregel.


## Inleiding {#cm-escalation-intro}

In dit document worden de ondersteunende procedures voor ernstige incidenten beschreven (**ERNST 1** niveau) die van invloed zijn op Adobe Primetime-authenticatie, Primetime Concurrency Monitoring en zijn partners.

## Definitie van escalatieniveau 1 niveau {#defn-escl-sevrityone-level}

A **ERNST 1** incident op niveau is **LEVEN** situatie, **in de productieomgeving**, waardoor de verificatie- en/of machtigingsstromen voor één kanaal en één MVPD niet kunnen worden voltooid, wat een groot aantal abonnees van de MVPD die de stroom uitvoeren, betreft.

## Voorbeelden van incidenten met prioriteitsgraad 1 {#exampl-sevone-incident}

* Productietoegang ingeschakeld bij <http://entitlement.auth.adobe.com/entitlement/AccessEnabler.js> is niet beschikbaar.

* Voor een specifieke MVPD, richt Adobe niet meer de login pagina opnieuw/toont, nadat de gebruiker MVPD (in om het even welke gesteunde browsers) selecteert.

* De partner ontvangt een groot aantal rapporten dat de gebruikers niet met specifieke MVPD kunnen voor authentiek verklaren/machtigen.

* Tijdens het verificatieproces zit de gebruiker vast op een Adobe-foutpagina zonder de mogelijkheid om de verificatie-/autorisatiestroom opnieuw te starten.


## Voorbeelden van *NOT* een incident met prioriteitsniveau 1 {#exampl-not-sev1}

*Voor dit soort kwesties zal Adobe onderzoek ondersteunen, maar het zijn geen incidenten van ernst 1:*

* Een of enkele abonnees kunnen de stroom niet uitvoeren vanwege een Flash-versieprobleem (ontbrekende Flash, Flash-blokkeerders, onjuiste Flash-versie).
* Een of enkele abonnees kunnen niet verifiëren en blijven op de MVPD-aanmeldingspagina.
* Een of enkele abonnees zijn geverifieerd, maar kunnen geen video&#39;s afspelen.
* Een/paar/alle abonnees ondervinden een JavaScript-fout op de programmeersite.

## Prioriteit 1 Escalatiestromen {#sevone-escalation-flows}

Ernst 1-incidenten kunnen worden geïnitieerd door Adobe of een Adobe Primetime-verificatiepartner. De stappen voor elk worden hieronder weergegeven.

### Door partners geïnitieerde stroom {#partner-initiated-flow}

1. De partner identificeert een incident met prioriteitsniveau 1 (zoals hierboven beschreven) dat onmiddellijk aandacht vereist.

1. De partner verzendt een e-mail naar tve-support@adobe.com met daarin &quot;URGENT - INCIDENT&quot; in de onderwerpregel en voegt de volgende informatie toe:

   * Titel
   * Beschrijving en stappen om te reproduceren
   * OS
   * Browser
   * Flash-versie
   * (optioneel) Alle beschikbare schermafbeeldingen of video-opnamen die het probleem aantonen

1. Als Adobe niet binnen 30 minuten aan het kaartje antwoordt, roept de partner het hieronder aantal:

   * **1-205-693-9813**


**Als u &quot;URGENT-INCIDENT&quot; niet opneemt in de titel van het ticket, wordt het niet opgepikt door ons meldingssysteem.**

### Door Adobe geïnitieerde stroom {#adobe-initiated-flow}

**...voor een Adobe Primetime-verificatieprobleem**

1. Adobe identificeert een interne kwestie en opent een kaartje met ons volgsysteem.

1. Adobe brengt de het programmamanager en technische contact van de partner op de hoogte, specificerend het kaartjesaantal en het geschatte effect van de kwestie.

1. Adobe werkt aan de oplossing van het incident en houdt alle betrokken partners op de hoogte.


**...voor een partnerkwestie (Programma/MVPD)**

1. Adobe stelt een probleem vast dat verband houdt met de integratie met een MVPD of op een van de sites van de programmeur.

1. Adobe brengt de beïnvloede partner op de hoogte **na de ondersteunende procedures die met die partner van kracht zijn** en opent een kaartje met de de steunorganisatie van de partner.

1. Als Adobe tijdens de effectbeoordeling vaststelt dat de kwestie tot een van de vooraf overeengekomen besluiten over incidentscenario&#39;s behoort (zie de paragraaf &quot;Vooraf overeengekomen besluiten over incidentscenario&#39;s&quot; hieronder), zal zij dienovereenkomstig handelen zonder op partner1 te wachten. -invoer.

1. Adobe zal op updates van de partner en een bericht van de partner wachten wanneer de dienst is hersteld.

### Vooraf overeengekomen besluiten inzake incidentscenario&#39;s {#pre-agreed-decisions}

Er zijn situaties waarin een standaardhandeling wordt uitgevoerd in het geval dat dat scenario zich voordoet:

|    | Scenario | Beschrijving | Handelingen |
|:---:|:---|:---|:---|
| S1 | Adobe stelt vast dat er een probleem is met de integratie van een MVPD tijdens normale productieactiviteiten. | Tijdens normale productieactiviteiten, identificeert Adobe een probleem met één van de MVPD&#39;s die het uitvoeren van de authentificatie/vergunningsstromen onmogelijk maakt (b.v. verlopen certificaten, verlopen SAML reacties, gesloten havens, veranderde parameters, enz.) | Adobe zal de betrokken MVPD en programmeurs op de hoogte brengen. Adobe deactiveert dit MVPD voor alle betrokken programmeurs. Adobe zal een ticket openen met het MVPD volgens de overeengekomen steunprocedure met dat MVPD |
| S2 | Adobe activeert een nieuwe MVPD voor een Programmer, en de programmeur whitelists MVPD vóór de lanceringsdatum. | Adobe activeert een nieuwe MVPD voor de plaats van een Programmer, en de plaats toont nieuwe MVPD reeds in de plukker, zelfs als het niet verondersteld was. | Adobe zal de programmeur vóór de geplande datum in kennis stellen van de nieuwe MVPD die in de kiezer wordt weergegeven. De programmeur zal actie ondernemen om het uit de plukker indien nodig te verwijderen. |
| S3 | Adobe activeert een nieuwe MVPD voor een Programmer zelfs als MVPD niet klaar is om in productie te gaan | Adobe activeert een nieuwe MVPD voor een Programmer, maar MVPD heeft nog niet de steun voor de integratie opgesteld zodat kunnen de authentificatie/de vergunningsstromen niet worden uitgevoerd | Adobe zal de plaatsing slechts doen indien gevraagd door de programmeur De programmeur zal verantwoordelijk zijn voor het verzekeren van whitelisting van MVPD zodra alle tests werden uitgevoerd. |

### Responsverwachtingen voor incidenten met prioriteitsniveau 1 {#response-expectations}

* Eerste antwoord: 30 minuten (24/7)
* Actieplan: 1 uur (24/7)
* Resolutie: ASAP (24/7)
