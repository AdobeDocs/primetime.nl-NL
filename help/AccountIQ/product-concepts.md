---
title: Woordenlijst Account IQ
description: 'Een verklarende woordenlijst van productterminologieën.  '
source-git-commit: 8d8aa00d693b1ca7f960a71b40053e47249c63e4
workflow-type: tm+mt
source-wordcount: '1455'
ht-degree: 0%

---

# Productconcepten en woordenlijst {#glossary}

Verwijs de volgende productterminologieën en hun definities.

## Waarschijnlijkheid voor het delen van accounts {#account-sharing-probability-def}

Een dashboardpaneel met grafieken die de huidige segmenten die scores delen, verdeelt in het delen van bereikcategorieën van Zeer laag, Laag, Matig, Hoog en Zeer hoog.

## Handeling {#action-def}

Een directe of indirecte gebeurtenis in verband met een [Bewerking](#operation-def) die van invloed is op de kenmerken (bijvoorbeeld de score voor delen of het aantal gebruikte apparaten) van een verwant bewerkingssegment (of cohort).

## Geaggregeerde score voor delen {#sharing-probability-level-def}

Een dashboardpaneel met grafieken die de huidige segmenten die scores delen in het delen van waaiercategorieën van Zeer Laag, Laag, Matig, Hoog, en Zeer hoog, samen met elk categoriepercentage van de totale hoeveelheid het stromen voor het segment verdelen.

## AuthN {#authn-def}

Verificatie of het aantal verificatiepogingen. Een authentificatiepoging is het proces waarbij een gebruiker zonder een momenteel geldige authentificatiestatus aan hun gekozen MVPD wordt opnieuw gericht, waar zij zich aan MVPD - typisch met een gebruikersbenaming en een wachtwoord identificeren.

## AuthN OK {#authn-ok-def}

Het aantal geslaagde verificaties. Een succesvolle authentificatie komt voor wanneer een gebruikers zich identificeren door MVPD wordt bevestigd en in de gebruiker leidt terug naar programmeur app of plaats.

## AuthZ {#authz-def}

Vergunning of het nummer van de vergunningsaanvraag. Een autorisatieverzoek is het proces waarbij een programmeur toestemming van een MVPD door Adobe vraagt beginnen streaming de gevraagde inhoud van een gebruiker. Het MVPD verleent typisch het verzoek dat op de inhoudsrechten wordt gebaseerd verbonden aan het abonnement van de gebruiker MVPD (bijvoorbeeld of het kanaal verbonden aan de inhoud in het abonnement van de gebruiker is). Sommige antwoorden van het vergunningsverzoek worden in het voorgeheugen ondergebracht door Adobe, die Adobe toestaat om onmiddellijk te antwoorden zonder het verzoek tot MVPD over te gaan.

## AuthZ OK {#authz-ok-def}

Het aantal geslaagde toelatingen.

## Kanaal {#channel-def}

Kanaal, ook bekend als eigenschap, is een thematisch gerelateerde bron van video-inhoud. Traditioneel die een verschillende, numeriek adresseerbare ononderbroken videovoer van een MVPD vertegenwoordigen. Het kanaal wijst rechtstreeks aan een toegankelijk kanaal van inhoud beschikbaar aan de abonnees door hun Reeks Top Box (STB) toe.

## Cluster {#cluster-def}

Een cluster is een verzameling locaties en apparaten. De clusters worden gemaakt door gemeenschappelijke locaties tussen apparaten te zoeken. De apparaten die in een gemeenschappelijke plaats zijn gezien zullen worden beschouwd als om in de zelfde cluster te behoren. Twee apparaten kunnen in de zelfde cluster zijn alhoewel zij geen gemeenschappelijke plaatsen hebben maar door de plaatsen van andere apparaten kunnen worden aangesloten.

### Mobiele cluster {#mobile-cluster-def}

Een cluster zonder statische apparaten.

### Statische cluster {#static-cluster-def}

Een cluster met ten minste één statisch apparaat.

## Gelijkend {#consurrency-def}

De gelijktijdige uitvoering wordt gedefinieerd door twee (of meer) streams die tegelijkertijd of zeer dicht in de tijd worden afgespeeld, zodat het interval tussen de streams niet kan worden gerechtvaardigd door een normale snelheid te gebruiken.
Gelijktijdig gebruik wordt berekend met de maximale snelheid (mijl/uur) tussen twee verschillende clusters. Een gebruiker wordt geacht gelijktijdig gebruik te hebben als hij een snelheid van meer dan 124 m/h heeft op een afstand van minder dan 124 mijl of als hij een snelheid van meer dan 400 m/h heeft op een afstand van meer dan 124 mijl. De afstand wordt berekend tussen plaatsen van verschillende clusters. Gelijktijdig gebruik is toegestaan in dezelfde cluster.

## Apparaat {#device-def}

Een digitaal videohardwareproduct dat tv-inhoud overal kan afspelen en dat door Adobe Pass wordt ondersteund. Bijvoorbeeld smartphones, laptop- en desktopcomputers, spelconsoles en smartphones.

## Geografisch bereik {#geographical-span-def}

De afstand tussen de verste punten in een set locaties.

## Korreligheid {#granularity-def}

de grootte van de periode ten opzichte van het tijdsbestek; zoals een week of een maand.

## Gemiddelde industrie-index {#industry-avg-index-def}

Een waarde die voor elk van de Risicocijfers (Rekeningen, Gebruik, Algemeen) over alle Programmers en MVPDs tijdens het geselecteerde tijdkader wordt berekend.

## IP {#ip-def}

Het adres van het Internet-protocol dat aan een apparaat door een Dienstverlener van Internet wordt toegewezen. Bijvoorbeeld, kabeldienstverlener, en de leverancier van de celdienst.

## Isolatiemodus {#isolation-mode-def}

Een type van het delen analyse waar de evaluatie van een rekening tot gebeurtenissen beperkt is die direct op de programmeurs in het geselecteerde segment voorkwamen.  Normaliter worden alle accountgebeurtenissen geëvalueerd, wat een veel nauwkeuriger schatting van het delen biedt.  Sommige MVPD-gegevens zijn zodanig gestructureerd dat alleen de analyse van de isolatiemodus mogelijk is.

## Locatie {#location-def}

Een uniek punt op aarde. Het wordt ook de geolocatie genoemd voor een specifieke spelaanvraag, gedetecteerd met behulp van de gegevens van de pas, met een precisie van 1000mx1000m (één vierkante km).

<!-- ### Home location {#home-location-def}

the precision is 0.01 ~ 2000mx2000m (4 square km) - at this moment the home location is detected using an ML algo, based on data provided by two mvpds. The probability is ~ 80%. We are not using the zip code for the majority of the users. Currently, this information is not used in assessing the sharing probability. -->

## Media Company {#media-company-def}

Het Bedrijf van media is een bedrijf dat een groep media netwerken bezit.

## Metrisch {#metric}

Metric is een attribuut van abonneerekening (bijvoorbeeld, hun MVPD, de programmeurs en de kanalen van de inhoud zij stromen, het aantal apparaten zij gebruiken).

## Mobiel apparaat {#mobile-device-def}

Een apparaat met hoge mobiliteit. Bijvoorbeeld mobiele telefoon en tablet.

## MVPD {#mvpd-def}

MVPD, ook gekend als Verdeler, is aggregator, reseller, en verdeler van de video-inhoud van het Bedrijf van Media.

## Bewerking {#operation-def}

Bewerking is een record die is gemaakt om het effect van een bepaalde bewerking bij te houden [action](#action-def) op een bijbehorend segment. Een voorbeeld van een actie kan een grens zijn die op het aantal gezamenlijke stromen wordt geplaatst toegestaan voor rekeningen die door het segment worden geïdentificeerd.

## Algehele score voor delen {#overall-sharing-score}

Een waarde die gebruikers helpt de omvang van het delen van wachtwoorden op de eigenschappen van de Programmer of door abonnees begrijpen MVPD en hen een gevoel van urgentie verstrekken om op het te handelen.

<!--**Aggregated Risk Index**
Also known as Risk Index and Sharing Risk Index, it is a value that helps users understand the magnitude of password sharing on Programmer properties or by MVPD subscribers and provides them a sense of urgency to act upon it.-->

<!--**Risk Index - Overall**
A value computed as an average of "Risk Index - Accounts" and the "Risk Index - Usage". Overall Sharing Risk Index-->

## Aanvraag afspelen {#play-requests-def}

Een verzoek dat door een client-app of -site aan Adobe is gedaan om een mediatoken aan te vragen om een streamstart op te nemen en te beveiligen.

## Programmeur {#programmer-def}

Programmeur, ook bekend als Netwerk, is een bedrijf dat dochteronderneming is van een groter bedrijf (bedrijf) dat één of meerdere kanalen bezit en beheert.

## aanvragerID {#requestorid-def}

Identiteitskaart een Bedrijf van Media gebruikt om zich of een dochteronderneming aan een MVPD te identificeren.  Afhankelijk van de implementatie van de Programmer, kon dit aan een Bedrijf van Media, een Programmer of een Kanaal in kaart brengen.  De meest gebruikelijke id die een mediabedrijf gebruikt om zichzelf of een dochteronderneming van een MVPD te identificeren.  Afhankelijk van de implementatie van de Programmer, kon dit aan een Bedrijf van Media, een Programmer of een Kanaal in kaart brengen.  Dit is traditioneel toegewezen aan een kanaal.  Met de verwezenlijking van pseudo-Kanalen zoals MML (Maart Madness Live) en technisch gedreven bewegingen om MVPD-gedreven gegevensbeperkingen te richten, begint requestID meer met het Bedrijf van Media te worden geassocieerd.

## resourceID {#resource-id-def}

De inhoud die door de eindgebruiker wordt aangevraagd.  Traditioneel is hiermee de Kanaal-koppeling geïdentificeerd die is gekoppeld aan de inhoud die de gebruiker heeft aangevraagd.  Dankzij systeemverbeteringen kan die id specifieke programma&#39;s vertegenwoordigen (bijvoorbeeld met specifieke classificaties), maar de id blijft het bijbehorende kanaal identificeren.

## Risicoindex - gebruik {#risk-index-usage}

Deze waarde, ook wel bekend als Gebruik van gedeelde accounts, wordt berekend op basis van het aantal afspeelverzoeken dat door elke account is ingediend, gewogen op basis van de waarschijnlijkheid dat elke account wordt gedeeld. Dit wordt ook wel &#39;Gebruik door gedeelde accounts&#39;-risicoindex genoemd.

## Segment {#segmet-def}

Segment is een set accounts die voldoen aan de door de gebruiker gedefinieerde voorwaarden die worden bepaald door de geselecteerde meetgegevens (bijvoorbeeld &quot;gebruikers van MVPD A, B, C, D of E die kanalen X, Y of Z hebben gecontroleerd&quot;).

## Niveau voor delen {#sharing-level-def}

Ook genoemd geworden Index van het Risico - rekeningen of de Index van het Risico van Gedeelde Rekeningen, is het een waarde die op een gemiddelde van de het delen waarschijnlijkheid wordt berekend die voor elke rekening in de reeks geselecteerde MVPDs wordt berekend die van één van de geselecteerde Kanalen van de Programmer tijdens het geselecteerde tijdkader heeft gestroomd.

## Statisch apparaat {#static-device-def}

Een apparaat met een zeer lage mobiliteit. Voorbeeld: spelconsole, set top box en televisieset.

## Tijdskader {#time-frame-def}

Wordt ook wel periode- of tijdsleuf genoemd en dit is het tijdvenster waarin de activiteit van de afspeelaanvraag in de gebruikersinterface en tabellen van begin tot eind is opgenomen.

## Bovenste MVPD&#39;s in segment {#top-mvpds-def}

De bovenste (maximaal 10) MVPD&#39;s in het geselecteerde segment als maat door niveau delen, Gebruik van gedeelde accounts of Algehele score delen.

## Trend {#trend-def}

Het percentageverschil in bijbehorende metrisch (bijvoorbeeld, percentage van totale spelverzoeken) tussen de huidige en vorige periode.

## Unieke abonnees {#unique-subscriber-def}

Het aantal unieke MVPD-accounts voor een bepaalde periode dat gedurende een bepaalde periode heeft samengewerkt met programmeur TV Anywhere apps of sites waarbij Adobe Pass is betrokken.  Die interactie omvat elke activiteit op de programmeur-app of -site die resulteert in een aanroep naar een Adobe Pass-service. Bijvoorbeeld het controleren van de status authN of authZ, het voor authentiek verklaren en het machtigen. Het totale aantal unieke abonnees zal ook het aantal unieke apparaten omvatten als het gebruik van Adobe TempPass (dat vrije voorproef) van programmeurs deel van het segment uitmaakt.

## Gebruik {#usage-defs}

### Geanimeerde gebruiker {#avid-user-def}

Meer dan 37 spelverzoeken per maand.

### Onfrequente gebruiker {#infrequent-users-def}

Minder dan 9 verzoeken om afspelen per maand.

### Gewone gebruiker {#regular-user-def}

Van 9 tot 37 verzoeken per maand afspelen.

## Gebruikspatroon {#usage-patern-def}

Een eindige set categorielabels die op een account wordt toegepast en die de gebruikers van de account het best karakteriseert in termen van sociale groepen of gedrag (bijvoorbeeld een klein gezin, een reiziger of een forenmaker, sociaal delen, enz.).

## Postcode {#zip-code-def}

De Amerikaanse postcode die is gekoppeld aan locaties in de VS
