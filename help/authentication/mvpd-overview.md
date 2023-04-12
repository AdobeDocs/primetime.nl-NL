---
title: Overzicht voor MVPDs
description: Overzicht voor MVPDs
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '2736'
ht-degree: 0%

---


# Een overzicht van MVPD&#39;s {#mvpd-overview}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding {#intro}

Dit overzicht is bedoeld voor Multichannel Video Programming Distributors (MVPD&#39;s). Zie de sectie Verwante informatie aan het einde van dit document voor aanvullende documentatie, waaronder de handleidingen Kickstart en Integration.



TV Overal (TVE) is de bekende branchebeweging die betaaltelevisie-abonnees toegang biedt tot de inhoud die zij al betalen, op meerdere apparaten, zowel in als uit hun huizen.  Voor betaaltelevisieproviders creëert TVE nieuwe mogelijkheden, zowel om bestaande klantenrelaties te behouden als om nieuwe relaties mogelijk te maken. Maar samen met deze kansen komen er uitdagingen. In het landschap van TVE, verstrekken de programmeurs de inhoud, maar MVPDs houdt de klanteninformatie voor het verifiëren dat de potentiële kijkers geldige abonnees zijn.



Het coördineren van de authentificatie en de vergunning van de kijker met één Programmer kan ongecompliceerd zijn, maar het coördineren met tientallen of honderden verschillende Programmers wordt steeds complexer. Met Adobe® Pass hoeven MVPD&#39;s echter slechts één eenvoudige integratie te implementeren om toegang te krijgen tot het gehele TVE-ecosysteem, inclusief Programmers zoals NBCUniversal Media, Turner Broadcasting (TBS, TNT, CNN), Fox Broadcast Networks, Hulu enzovoort.  Adobe Primetime-verificatie biedt een integratieframework dat het bepalen van gebruikersrechten eenvoudig en veilig maakt.



Onderste regel: Met Adobe Primetime-verificatie worden machtigingstransacties tussen programmeurs en MVPD&#39;s veilig gemedieerd, waardoor de gebruiker gemakkelijker toegang heeft tot abonnementsinhoud. Met andere woorden, Adobe Primetime-verificatie maakt het voor de juiste klanten eenvoudig en snel om toegang te krijgen tot de juiste inhoud.


Bij Adobe Primetime-verificatie ontvangen MVPD&#39;s:

Eenvoudige integratie met programmeurs.  Onmiddellijke connectiviteit van veelvoudige inhoudseigenaars met één enkele integratie leveren.

Verbeterde betrokkenheid van klanten.  Ondersteuning voor een vloeiende merkboodschap aangezien uw klanten inhoud op meerdere platforms en apparaten bekijken.

Beveiligde verificatie.  Zorg ervoor dat alleen geautoriseerde gebruikers en apparaten toegang krijgen tot premiuminhoud en (optioneel) beperk het aantal apparaten en gelijktijdige streams dat per huishoudelijke account kan worden aangesloten.

## Veelgestelde vragen {#faq}

Hoe veilig is Adobe Primetime-verificatie? De belangrijkste prioriteit van de Adobe Primetime-verificatiearchitectuur is ervoor te zorgen dat alleen geautoriseerde viewers worden geverifieerd en toegang krijgen tot premiuminhoud. Adobe Primetime-verificatie biedt een nauwe band met toegang tot weergaveapparaten en kan helpen streams, sessies en/of apparaten voor een bepaald huishouden te beperken.


Is Flash Player vereist? Adobe Primetime-verificatie voor tv. Overal is een speler en een platform geavanceerd, die worden geïntegreerd met elke afspeeltoepassing, inclusief Silverlight en HTML5. Bovendien biedt Adobe Primetime-verificatie native ondersteuning voor apparaten zoals telefoons en tablets met iOS en Android.


Welke apparaten worden door Adobe Primetime-verificatie ondersteund? Adobe Primetime-verificatie wordt door vrijwel elk apparaat ondersteund met de HTML5-webkit voor weergave in de browser. Bovendien wordt bij Adobe Primetime-verificatie de implementatie van native software-ontwikkelingskits (SDK&#39;s) voortgezet voor verschillende apparaatspecifieke platformen, zoals iOS, Android™, Xbox360 (Afgekeurd) en Adobe AIR® (Afgekeurd) toepassingen. Recentelijk heeft Adobe Primetime-verificatie een oplossing zonder clips ontwikkeld voor apparaten die geen browserpagina&#39;s kunnen renderen (bijvoorbeeld &#39;slimme&#39; tv&#39;s, set-top boxes en spelconsoles).  De capaciteit om browser pagina&#39;s terug te geven is een vereiste om gebruikers met MVPDs voor authentiek te verklaren.


Steunt de authentificatie van Adobe Primetime de nieuwe normen voor TV overal? Adobe Primetime-verificatie is compatibel met de CableLabs OLCA-specificatie (Online Content Access), die technische vereisten en architectuur biedt voor de levering van video van online bronnen aan een Pay TV-klant. Adobe nam in juni 2011 deel aan het gezamenlijke CableLabs-interoptestproject en stemde in met het testproces voor een Service Provider-implementatie. Adobe Primetime-verificatie wordt geverifieerd (voltooid en getest) aan de hand van de OLCA-specificaties voor verificatie. De vergunningscomponent wordt voltooid, maar de testende controle wacht momenteel de versie van het CableLabs testende milieu. Adobe is ook actief lid van het OATC (Open Authentication Technical Consortium) en neemt als onderdeel van dat orgaan deel aan diverse specificatieontwerpprojecten van de subcomités.



Wat is verificatie? De authentificatie is het proces waarin een MVPD bevestigt dat een bepaalde gebruiker een bekende klant is.



Wat is autorisatie? De vergunning is het proces waarin een MVPD bevestigt dat een voor authentiek verklaarde gebruiker een geldig abonnement op een bepaalde middel heeft.



## Architectuur {#architecture}

De authentificatie van Adobe Primetime is de ontvangen dienst die snelle (server aan server) integratie toestaat die op de bedrijfsregels door zowel MVPDs als Programmers wordt vereist. Dit betekent een snelle marktintroductie voor alle partijen, een veiliger omgeving om fraude te voorkomen en een superieure klantervaring, met meer tv-inhoud die beschikbaar is voor meer mensen op meer platforms.


Adobe Primetime-verificatie wordt aangeboden via het SaaS-model (Software as a Service) en maakt een veiligere communicatie mogelijk tussen eindgebruikers, MVPD&#39;s en programmeurs, om machtigingen voor inhoud te valideren. De kerncomponenten van de dienst omvatten het volgende:

Server-zijde - De gehoste Adobe Primetime-verificatieserver. Dit is een toepassingsserver die in achterkanaal (server-aan-server) communicatie met de authentificatiesystemen van MVPDs in dienst neemt.
Client-kant: De client-side Access Enabler - De Access Enabler is een klein bestand dat in de webpagina of spelertoepassing van een programmeur wordt geladen. Het verstrekt machtiging APIs aan de inhoud die van de Programmer toepassing bekijkt, en communiceert met de de authentificatieserver van Adobe Primetime.
Clientloze webservices (voor apparaten die niet geschikt zijn voor het web) - RESTful-webservices die API&#39;s met machtigingen bieden voor apparaten zoals slimme tv&#39;s, spelconsoles en set-top boxes.

>[!NOTE]
>
>Als MVPD, moeten uw Webdiensten verzoeken om authentificatie en vergunning van de authentificatie van Adobe Primetime kunnen erkennen en met de vereiste gegevens in het verwachte formaat antwoorden.

Met Adobe Primetime-verificatie kunt u klanten een gefederaliseerd identiteitsbeheer bieden, ook wel SSO-verificatie (Single Sign-On) genoemd. Met de authentificatie van Adobe Primetime, is er geen behoefte voor abonnees om opnieuw aan te melden na hun eerste authentificatie, zolang die authentificatie door MVPD wordt toegestaan om te blijven. (Doorgaans 30 dagen.) Om dit te verwezenlijken, verstrekt de authentificatie van Adobe Primetime een gemeenschappelijk domein voor authentificatietokens voor onze klanten. Deze informatie van de authentificatiestatus is beschikbaar aan alle deelnemende plaatsen die met een bepaalde MVPD geïntegreerd zijn.


Momenteel, gebruiken de meeste de authentificatieintegratie van Adobe Primetime met MVPDs het protocol van SAML, één van de primaire authentificatienormen. De authentificatie van Adobe Primetime doet dienst als volmachtDienstverlener in de architectuur van SAML en handhaaft de authentificatiereactie van SAML als veilig teken in het gemeenschappelijke domein van de Adobe. Adobe Primetime-verificatie is compatibel met SAML 2.0. Nochtans, terwijl de authentificatie van Adobe Primetime typisch met de oplossingen van SAML SSO op dit punt wordt gebruikt, is de de authentificatiearchitectuur van Adobe Primetime niet gebonden aan om het even welk specifiek protocol. Daarom kan de steun voor nieuwe protocollen - zoals die op OAuth 2.0 of douaneprotocollen worden gebaseerd - in tijd worden toegevoegd.


Adobe werkt samen met het technische team van een MVPD om Adobe Primetime-verificatie te configureren om aan de behoeften van bestaande integratie te voldoen. De integratie is gratis voor MVPD&#39;s, uitgaande van een &quot;standaard&quot; integratie en minimale supportvereisten (documentatie en standaard e-mailondersteuning). Als een MVPD significante steun of een geëscaleerde chronologie vereist, kan een steunprijs worden in rekening gebracht, of de leverancier kan met een derde willen werken vertrouwd met onze oplossing zoals Synacor.


De authentificatie van Adobe Primetime steunt ook de efficiënte behandeling van MVPD bedrijfslogica, als volgt:

Voor bedrijfslogica die op zichzelf staand is en door MVPD kan worden toegepast wanneer een verzoek om toestemming wordt ontvangen, verstrekt Adobe de noodzakelijke gegevens die worden vereist om de bedrijfslogische handhaving te steunen wanneer MVPD een vergunningsverzoek ontvangt. Deze gegevens kunnen, maar zijn niet beperkt tot, unieke apparaat-id voor de gebruiker die het verzoek indient en het IP-adres van het apparaat bevatten.

Voor bedrijfslogica die gebruikersinterventie en/of specifieke behandeling door de oplossing van Adobe vereist, kan Adobe sommige douaneeigenschappen voor elke MVPD handhaven. Deze MVPD-specifieke configuraties/beleid omvatten het toelaten van vooraf bepaalde werkschema&#39;s die op specifieke punten van het top-level werkschema kunnen worden afgezet. Neem voor meer informatie over ondersteuning van aangepaste eigenschappen contact op met uw Adobe-vertegenwoordiger.

Het volgende diagram illustreert de verhouding van MVPD en Programmer met deze de authentificatiecomponenten van Adobe Primetime:

![](assets/high-level-architecture-nflows.png)

*Afbeelding: Architectuur en stromen op hoog niveau*

## Adobe Primetime-verificatiecomponenten {#components}

Hieronder vindt u een overzicht van enkele van de belangrijkste onderdelen van het Adobe Primetime-verificatiesecosysteem. Deze omvatten:

* [De Diensten van het Web van de Toegang toelaten/Clientless](#ae)
* [De op Adobe gehoste back-endserver](#backend)
* [Tokens](#tokens)

### Toegang tot webservices zonder client {#ae}

De Toegangsmanager vergemakkelijkt alle authentificatie en vergunningsinteractie met de gebruiker en loopt plaatselijk op hun systeem. Het is Toegangsbeheer die de daadwerkelijke machtigingswerkstromen met MVPD behandelt, terwijl de programmeur verantwoordelijkheid voor de hoger-vlakke Web-pagina of spelertoepassing handhaaft.

Webservices zonder client worden geleverd door Adobe Primetime-verificatie voor apparaten die geen webpagina&#39;s kunnen weergeven.  Voor deze apparaten, wordt het machtigingsproces in werking gesteld en de inhoud bekeken op het slimme apparaat, terwijl de authentificatie met een MVPD op een web-geschikt apparaat (PC, smart-phone, en tablet) plaatsvindt.

Toegangsfunctie:

* Initieert MVPD-specifieke authentificatie en vergunningswerkschema&#39;s.
* Beheert de succesvolle vergunningsreacties per middel/kanaal van de Programmer om onnodig verzoekverkeer te minimaliseren.
* Kan voor vooraf bepaalde werkschema&#39;s specifiek voor elke MVPD, zoals expliciete apparatenregistratie worden gevormd.
* Het is beschikbaar in de volgende vormen:
   * Een SWF-bestand dat de Flash Player-runtime kan uitvoeren
   * Een JS-bestand dat rechtstreeks door de browser wordt uitgevoerd
   * Een native toegangsfunctie voor verschillende platforms, waaronder iOS, Android en Xbox.

### Op Adobe gehoste back-endserver {#backend}

De Adobe Primetime-verificatieback-endserver, gehost door Adobe:

* Bepalingen de authentificatie en vergunningswerkschema&#39;s met MVPDs die server-aan-server mededeling tussen de authentificatie van Adobe Primetime en de exploitant vereisen.
* Handhaaft de configuratie voor de plaatsen en de toepassingen van de Programmer.
* Gastheren de downloadbare de componentendossiers van Enabler van de Toegang.
* Genereert verificatie- en autorisatietokens.

### Tokens {#tokens}

De Adobe Primetime-oplossing voor verificatiebevoegdheden richt zich op het genereren van specifieke gegevens die worden verkregen wanneer de workflows voor verificatie en autorisatie met succes zijn voltooid. Deze gegevens worden tokens genoemd. Ze hebben een beperkte levensduur en worden veilig opgeslagen op platformafhankelijke locaties. Na afloop moeten tokens opnieuw worden uitgegeven door de workflows voor verificatie en/of autorisatie opnieuw te starten.

Er zijn drie soorten tokens die tijdens de authentificatie/vergunningswerkschema&#39;s worden uitgegeven. Twee zijn &quot;van lange duur,&quot;die continuïteit in de kijkervaring van de gebruiker verstrekken. Het derde, een korte token, biedt ondersteuning voor best practices van de branche om fraude te beperken door middel van streaming ripping. De time-to-live (&quot;TTL&quot;) waarden voor tokens worden ingesteld op basis van overeenkomsten tussen MVPD&#39;s en programmeurs. U besluit over een waarde van TTL die het best uw zaken en uw klanten dient.

**Het lange-levende authentificatietoken**. Verificatie is geslaagd wanneer een klant Adobe Primetime-verificatie gebruikt om zich met succes aan te melden bij zijn MVPD-account. De authentificatie van Adobe Primetime veroorzaakt dan een lang-levende authentificatie (&quot;authN&quot;) teken verbonden aan het het vragen apparaat en (afhankelijk van MVPD) een globally uniek herkenningsteken (&quot;GUID&quot;) dat anoniem de gebruiker identificeert.

**Token voor langlevende vergunningen**. Na een geslaagde autorisatie maakt Adobe Primetime-verificatie een token voor een langdurige autorisatie (&quot;authZ&quot;). Dit token is niet overdraagbaar omdat het is gekoppeld aan het verzoekende apparaat en een specifieke beveiligde bron (bijvoorbeeld een kanaal, serie of aflevering). Toegangsbeheer gebruikt het lange-levende authZ teken om de kortstondige media tokens tot stand te brengen die voor daadwerkelijke het bekijken toegang worden gebruikt.

**Het media-token voor korte tijd**. Zodra de gebruiker wordt toegelaten, produceert de authentificatie van Adobe Primetime een authZ teken, en gebruikt dat teken om een enig-gebruik, kortlevend media teken te produceren dat door Adobe wordt ondertekend en wordt gecodeerd om het knoeien tijdens uitwisseling te vermijden. Omdat het kort-levende teken aan de het inbedden plaats door of Toegangstoelage API of de Zonder Clienteuze Webdiensten wordt blootgesteld, alvorens toegang tot het beschermde middel te verlenen, moet de media server van de programmeur een de authentificatiecomponent van Adobe Primetime, de Symbolische Verifier van Media gebruiken, om het teken te bevestigen.

## Levenscyclus voor MVPD-integratie {#lifecycle}

In de volgende afbeelding ziet u de levenscyclus van de integratie tussen Adobe Primetime-verificatie en een MVPD.

![](assets/mvpd-int-lifecycle.png)

*Afbeelding: Levenscyclus van MVPD-integratie*

## Entitlement FlowGrafiek {#chart}

In het volgende stroomdiagram wordt het algemene proces beschreven voor het bevestigen van machtigingen met Adobe Primetime-verificatie:

![](assets/authn-authz-entitlmnt-flow.png)

*Afbeelding: Procedure voor bevestiging van rechten met Adobe Primetime-verificatie*

## Verificatiestappen {#authn-steps}

De volgende stappen geven een voorbeeld van de Adobe Primetime-verificatiestroom.  Dit is het deel van het machtigingsproces waarin een Programmer bepaalt als de gebruiker een geldige klant van MVPD is.  In dit scenario, is de gebruiker een geldige abonnee aan MVPD.  De gebruiker probeert beveiligde inhoud weer te geven met de Flash-toepassing van een programmeur:

1. De gebruiker bladert naar de Web-pagina van de Programmer, die de toepassing van de Flash van de Programmer en de componenten van de Toegelaten van de Authentificatie van Adobe Primetime op de machine van de gebruiker laadt. De toepassing van de Flash gebruikt Toegang Enabler om het herkennen van de programmeur met de authentificatie van Adobe Primetime te plaatsen, en de authentificatiepunten van Adobe Primetime de Toegankelijkheid met configuratie en staatsgegevens voor die programmeur (de &quot;aanvrager&quot;). De Toegangsfunctie moet deze gegevens van de server ontvangen voordat andere API-aanroepen kunnen worden uitgevoerd.  Technische opmerking: De programmeur stelt zijn identiteit met Toegangsmogelijkheden in `setRequestor()` methode; zie voor meer informatie de [Programmeringsintegratiehandleiding](/help/authentication/programmer-integration-guide-overview.md).
1. Wanneer de gebruiker probeert om de beschermde inhoud van de Programmer te bekijken, stelt de toepassing van de Programmer de gebruiker met een lijst van MVPDs voor, waarvan de gebruiker een leverancier selecteert.
1. De gebruiker wordt opnieuw gericht aan een de authentificatieserver van Adobe Primetime, waar een gecodeerd verzoek van SAML voor gebruiker-geselecteerde MVPD wordt gecreeerd. Dit verzoek wordt verzonden als authentificatieverzoek namens de programmeur aan MVPD. Afhankelijk van het systeem van MVPD, wordt browser van de gebruiker dan of opnieuw gericht aan de plaats van MVPD aan login, of een login iFrame wordt gecreeerd in app van de Programmer.
1. In beide gevallen (omleiding of iFrame) accepteert de MVPD de aanvraag en geeft de aanmeldingspagina weer.
1. De gebruiker login met MVPD, MVPD bevestigt de status van de gebruiker als betalende klant, en dan leidt MVPD zijn eigen zitting van HTTP.
1. Wanneer de gebruiker wordt bevestigd, leidt MVPD tot een reactie (SAML &amp; gecodeerd), die MVPD terug naar de authentificatie van Adobe Primetime verzendt.
1. Adobe Primetime-verificatie ontvangt de MVPD-reactie, ziet dat er een HTTP-verificatiesessie voor Adobe Primetime is geopend, valideert de [SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) reactie van MVPD, en richt terug naar de plaats van de Programmer.
1. De site van de programmeur wordt opnieuw geladen, de Access Enabler wordt opnieuw geladen en de programmeur roept setRequestor() opnieuw aan.  De tweede vraag aan setRequestor () is noodzakelijk omdat de huidige configuratie is veranderd-er nu een vlag aanwezig is die toelaat van de Toegang meedeelt dat een teken AuthN op de server wacht te worden geproduceerd.
1. Toegangsbeheer ziet dat er een verificatie in behandeling is en vraagt het token aan bij de Adobe Primetime-verificatieserver. Het token wordt opgehaald door de servermogelijkheden van Flash Player DRM aan te roepen.
1. Het teken AuthN wordt opgeslagen in het geheime voorgeheugen van Flash Player LSO van de Programmer; De verificatie is nu voltooid en de sessie wordt vernietigd op de Adobe Primetime-verificatieserver.

## Autorisatiestappen {#authz-steps}

De volgende stappen gaan verder op de vorige sectie ([Verificatiestappen](#authn-steps)):

1. Wanneer de gebruiker probeert om tot de beschermde inhoud van de Programmer toegang te hebben, controleert de toepassing van de Programmer eerst op een teken AuthN op de lokale machine of het apparaat van de gebruiker.  Als dat token niet aanwezig is, wordt het [Verificatiestappen](#authn-steps) hierboven worden gevolgd.  Als het token AuthN aanwezig is, gaat de machtigingsstroom verder met de toepassing van de programmeur die een aanroep van Access Enabler initieert met een verzoek om de weergaverechten van de gebruiker voor een specifiek item van beveiligde inhoud op te halen.
1. Het specifieke item van de beveiligde inhoud wordt vertegenwoordigd door een &quot;resource identifier&quot;.  Dit kan een eenvoudige tekenreeks of een complexere structuur zijn, maar in elk geval wordt de aard van de resource identifier vooraf overeengekomen tussen de programmeur en de MVPD.  De toepassing van de Programmer gaat het middelherkenningsteken tot Toegangstoegelaten over.  De Toegangsfunctie controleert op een AuthZ-token op de lokale computer of het lokale apparaat van de gebruiker.  Als het token AuthZ er niet is, geeft de Access Enabler het verzoek door aan de back-end Adobe Primetime-verificatieserver.
1. De de authentificatieserver van Adobe Primetime communiceert met het MVPDs vergunningseindpunt gebruikend gestandaardiseerde protocollen.  Als de reactie van MVPD erop wijst dat de gebruiker de beschermde inhoud mag bekijken, leidt de de authentificatieserver van Adobe Primetime tot een teken AuthZ en geeft het terug naar Enabler van de Toegang, die het teken AuthZ op de machine van de gebruiker opslaat.
1. Met een token AuthZ dat op de computer of het apparaat van de gebruiker is opgeslagen, roept de toepassing van de programmeur de Access Enabler op om een token van de Adobe Primetime-verificatieserver te verkrijgen en verstrekt deze token aan de toepassing van de programmeur.
1. Tot slot gebruikt de toepassing van de Programmeur de component van de Verificator van het Boek van Media om te bevestigen dat de juiste gebruiker de juiste inhoud bekijkt, en met het Symbolische teken op zijn plaats, wordt de gebruiker toegestaan om de beschermde inhoud te bekijken.

<!--
>![RELATEDINFORMATION]
>
>*   Kickstart Guides, [MVPD kickstart](/help/authentication/mvpd-kickstart-guide.md) and [programmer kickstart](/help/authentication/programmer-kickstart-guide.md). These guides explain the initial steps to take to begin integrating with Adobe Primetime authentication.
>
>*   [MVPD Integration Guide](/help/authentication/mvpd-kickstart-guide.md). This is a lower level technical guide for MVPDs, directed primarily to the software engineers who code and test the applications and systems involved in the integration.
>
>*   [Overview For Programmers](/help/authentication/programmer-overview.md). The same high level of conceptual information as in this MVPD overview, but directed toward the content providers (Programmers).
-->
