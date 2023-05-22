---
title: Kickstart-handleiding voor programmeurs
description: Kickstart-handleiding voor programmeurs
exl-id: 0aecdb81-9b97-4475-b0b0-654d916b2374
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# Kickstart-handleiding voor programmeurs {#programmer-kickstart-guide}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding {#prog-kickstart-guide-intro}

Welkom bij Adobe Primetime-verificatie voor tv overal. Wij kijken ernaar uit met u samen te werken.

>[!NOTE]
>
>Dit is de Kickstart Guide voor programmeurs (inhoudsproviders). Als u met een Multichannel Video Programming Distributor (MVPD) bent, gelieve zeker te zijn om te zien [MVPD kickstart-handleiding](/help/authentication/mvpd-kickstart-guide.md).


Adobe Primetime-verificatiecontacten:

* Ondersteuning - voor alle vragen, incidenten of functieverzoeken, `tve-support@adobe.com`
* Een contact van Enablement zal aan uw project tegen de tijd van uw projectkickoff worden toegewezen.

In de volgende informatie worden enkele belangrijke eerste stappen beschreven om een solide en efficiënt begin te maken. Het doel is om uitleg te geven en te verwachten over de manier waarop we met partners zullen samenwerken om integratie te bereiken. Houd voor elk object rekening met de onderstaande secties &#39;&#39;Je geeft&#39;&#39; / &#39;&#39;Adobe geeft&#39;&#39;. Deze worden vermeld als controlelijst, of gids aangezien wij door het project werken.

In dit document wordt ervan uitgegaan dat programmeurs zijn aangemeld om met een gekozen MVPD-partner te werken.

## Releaseplanning {#release-schedule}

De ontwikkelingscyclus van de sprint van de Adobe is gepland zodat u kunt zien wanneer onze releases gepland zijn en hoe elke release wordt bevorderd via ons ontwikkelingssysteem.

Nadat elke sprint volledig is is het beschikbaar voor QE, of om nieuwe implementaties op onze server van UAT te zien.

Ongeveer om de 6 weken zal een versie aan de Adobe pre-Kwalificatieserver worden gemaakt. (Dit is de server waar wij onze voorgestelde volgende versie terwijl het uitvoeren van definitieve QE houden.) Deze builds zullen al werk omvatten dat sinds de laatste druppel in de sprot is voltooid. Een venster QE van twee weken is beschikbaar op dit ogenblik voor partners om deze versie te testen.

Ervan uitgaande dat zich tijdens het vorige testvenster van twee weken geen kritieke problemen hebben voorgedaan, wordt de release bevorderd tot live productie. Dit betekent dat de integratie in het milieu van de Versie van de Adobe beschikbaar zal zijn, maar de partners kiezen wanneer zij de versie openbaar maken.

<!--For the latest release schedule information, see the Release Calendar.-->

## Ondersteuningsdocumentatie {#supp-doc}

Adobe verstrekt:

* Implementatiehandleiding: **`https://tve.zendesk.com/entries/498741-tve-deployment-guide`**
* Toegang tot ons Zendesk-systeem voor klantenondersteuning. Dit is ook waar u steekproeven, informatie en videoleerprogramma&#39;s over sommige processen kunt vinden. Als u dit document op Zendesk wilt openen, moet u zich samen met andere documenten die daar zijn gepost, registreren en een account maken op `https://tve.zendesk.com/home`. Er is geen limiet voor het aantal gebruikers dat u kunt registreren.  U kunt opmerkingen bekijken en delen op elk gearchiveerd ticket. Alle ondersteuningsvragen moeten worden gericht aan `tve-support@adobe.com`.
* [Programmeringsintegratiehandleiding](/help/authentication/programmer-integration-guide-overview.md)
* Bibliotheek van Media Token Verifier: `https://tve.zendesk.com/entries/471323-media-token-validator-library`.

## Setup testomgeving {#test-env-setup}

Adobe zal u eerst met de de testplaats van de Adobe beginnen, waar Adobe als MVPD voor testdoeleinden dienst doet. Uw team kan vervolgens een testwebsite instellen die de Adobe-API aanroept. Gebruik de standaardMVPD selecteur, en selecteer &quot;Adobe&quot;als idP.

U verstrekt:

1. Id van aanvrager. Dit is een tekenreeks waarmee het merk van de website of de toepassing die aanvragen voor Adobe Primetime-verificatie indient, op unieke wijze wordt geïdentificeerd. De tekenreeks zelf is willekeurig, maar moet tussen Adobe en programmeur worden overeengekomen
1. Kanaalgegevens. Dit is een set tekenreeksen waarmee wordt aangegeven welke inhoudskanalen door de aanvrager-id worden aangevraagd. In veel gevallen zijn het kanaal en de aanvrager-id hetzelfde. U kunt echter meerdere kanalen met inhoud hebben die door dezelfde id kan worden aangevraagd. De de naamkoorden van het kanaal zouden aan de kanalen van kabelTV moeten beantwoorden. Sommige MVPDs zal deze waarde over het protocol bevestigen AuthN en/of AuthZ.
1. Domeinnamen (toe te staan voor die aanvrager-id). Dit wordt een lijst met domeinnamen die door Adobe worden vermeld om de aanvrager-id te accepteren. Alleen goedgekeurde domeinen hebben dan toegang tot Adobe Primetime-verificatie met uw metagegevens. OPMERKING: domeinnamen die geldig zijn voor productie kunnen verschillen voor tests/ophaling en beide moeten worden verstrekt en geïdentificeerd.

Adobe zal de rekening opzetten en Adobe zal verstrekken:

* Aanmelding en wachtwoord voor toegang tot de testsite

## Instellen met MVPD {#setup-mvpd}

Deze sectie beschrijft wat u nodig hebt wanneer u van de de testplaats van Adobe aan het werk met MVPD migreert.

U zult (via MVPD) verstrekken:

* **Twee reeksen geloofsbrieven**:
   * AuthN + AuthZ : login/wachtwoord voor een gebruiker die voor authentiek en gemachtigd is
   * AuthN + Non-AuthZ : login/wachtwoord voor een gebruiker die voor authentiek maar niet geautoriseerd is
* **Resource ID**. Dit is een specifieke inhoudsidentificatie die met een MVPD over het protocol AuthZ zal worden bevestigd. Dit kan op het kanaal, toon, episode, of activaniveau zijn; hierover moet overeenstemming worden bereikt met uw MVPD.

De authentificatie van Adobe Primetime steunt een op MRSS-Gebaseerd meta-gegevensschema wat betekent dat identiteitskaarts van het Middel zo specifiek als nodig kan zijn, en herkenningstekens kan omvatten die aan specifieke MVPD uniek kunnen zijn.

**NIEUWE MVPD-integratie**: Het is belangrijk om te herinneren dat uw gekozen MVPD een integraal deel bij de voltooiing van om het even welke integratie speelt. Adobe moet code voor elke MVPD volgens hun specificaties schrijven. Totdat deze stappen zijn voltooid, kunt u die MVPD niet selecteren in het dialoogvenster of de producttests voltooien. Adobe moet dit werk vooraf plannen om in de volgende beschikbare sprint te passen. (Raadpleeg de releasekalender voor actuele informatie over de planning.)

**Bestaande MVPD-integratie**: Als uw gekozen MVPD reeds opstelling met Adobe is dan zouden de connectiviteitsstappen veel eenvoudiger (sneller) moeten zijn, en vaak kan de connectiviteit door configuratieveranderingen worden bereikt.

>[!NOTE]
>
>Het MVPD zal de programmeur nog steeds moeten toelaten en zich moeten aftekenen bij alle relevante zakelijke transacties.

**QE met MVPDs**: Bij alle integraties zal gezamenlijke kwantitatieve versoepeling nodig zijn en aangezien de eindgebruiker uiteindelijk een klant van de MVPD is, hebben velen testcycli ingesteld voordat ze &quot;live&quot; duwen. Aangezien dit het plannen van middelen MVPD impliceert, is dit een potentieel gebied voor vertraging.

<!--
>[RELATEDINFORMATION]
>[MVPD Kickstart Guide](help\authentication\mvpd-kickstart-guide.md)
-->
