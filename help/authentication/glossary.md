---
title: Verklarende woordenlijst
description: Verklarende woordenlijst
exl-id: e64a94f6-7460-4aa8-8d6b-e0553ba1e4ec
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Verklarende woordenlijst {#glossary}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## AccessEnabler {#accessEnabler}

De clientcomponent van Adobe Primetime-verificatie. Adobe Primetime-verificatie biedt een AccessEnabler-bibliotheek voor elk ondersteund platform.

## AuthN {#authn}

Wordt gebruikt als steno voor &quot;verificatie&quot;, zoals in &quot;AuthN Token&quot; of &quot;AuthN Flow&quot;.


## AuthN Token{#authn-token}

Verificatietoken, gegenereerd door Adobe Primetime-verificatie nadat een gebruiker is geverifieerd met een MVPD. Afhankelijk van het integratieplatform van de programmeur, wordt het token opgeslagen op het apparaat van de gebruiker of op de Adobe Primetime-verificatieservers.

## AuthZ {#authz}

Wordt gebruikt als steno voor &quot;autorisatie&quot;, zoals in &quot;AuthZ Token&quot; of &quot;AuthZ Flow&quot;.

## AuthZ Token {#authz-token}

Verificatietoken dat wordt gegenereerd door Adobe Primetime-verificatie nadat een gebruiker is gemachtigd om beveiligde inhoud weer te geven. Het token AuthZ wordt opgeslagen op Adobe Primetime-verificatieservers en wordt gebruikt om een [Token voor kortlevende media](#short-lived-token).

## Kanaal-id (afgekeurd) {#channel_id}

Voormalige term voor bron-id.

## Clientloze API {#clientless-api}

Een oplossing van de authentificatieintegratie van Adobe Primetime die de Webdiensten in plaats van de AccessEnabler cliëntcomponent gebruikt.

## Apparaat-id {#device-id}

Identificeert een apparaat op unieke wijze (zoals een telefoon, tablet, enz.) in Adobe Primetime-verificatie. Deze id is verkregen/opgegeven door de toepassing van de programmeur.


## Entitlement Flow{#entitlement_flow}

De term die wordt gebruikt in de verificatiedocumentatie van Adobe Primetime om te verwijzen naar het volledige proces van het registreren van een apparaat/gebruiker met Adobe Primetime-verificatie, het verifiëren van een gebruiker met een MVPD, het autoriseren van een bron voor een gebruiker en het afmelden van een gebruiker.


## GUID {#guid}

Zie [Gebruikersnaam](#user-id).

## IdP {#idp}

provider identificeren; synoniem met MVPD in de context van de rol van een MVPD in een de authentificatieintegratie van Adobe Primetime. (Klanten moeten hun identiteit verifiëren via de aanmeldingspagina van hun Pay TV-provider.)

## Verificator mediatokens {#media-token-verifier}

Een door Adobe verschafte bibliotheek die door Programmers wordt gebruikt om het kortstondige mediatoken te verifiëren dat door Adobe Primetime-verificatie wordt gegenereerd nadat een machtigingsstroom met succes is voltooid.

## MVPD {#mvpd}

Multi-channel Video Programming Distributor; synoniem met &quot;Pay TV Provider&quot;.

## MVPD-id {#mvpd-id}

Zie [Gebruikersnaam](#user-id).

## Partner-id {#partner-id}

Een herkenningsteken dat Adobe tot MVPDs overgaat, die het gebruiken om namens de authentificatie van Adobe Primetime te identificeren om authentificatie verzoekt. Soms wordt het gebruikt voor het vormen van hun UIs voor bepaalde Programmers, soms is het het zelfde over alle Programmers, hangt het van de behoeften van MVPD af.

## Tv-provider betalen {#pay-tv-provider}

Gelijk aan [MVPD](#mvpd).

## Programmeur {#programmer}

Gelijk aan &#39;contentprovider&#39;, &#39;account&#39;, &#39;kanaal&#39;, &#39;serviceprovider&#39;, &#39;merk&#39; enzovoort.

## Proxy MVPD {#proxy-mvpd}

een MVPD die identiteitsdiensten voor andere MVPDs verleent; direct geïntegreerd met Adobe Primetime-verificatie.

## Proxied MVPD {#proxied-mvpd}

Een MVPD die geen directe integratie met Adobe SP heeft, maar door een Volmacht MVPD geïntegreerd.

## Id van aanvrager {#requestor-id}

Hiermee wordt een [Programmeur](#programmer) (een account, merk, kanaal of eigenschap) binnen Adobe Primetime-verificatie. Deze id wordt bepaald door de programmeur en Adobe tijdens de eerste installatie van de account. Op het web is de aanvrager-id gekoppeld aan een reeks in een whitelisting opgenomen domeinen. om het even welke vraag die een identiteitskaart van een buitendomein gebruikt zal worden geweigerd. Programmeurs gebruiken de aanvrager-id ook voor analyses. Meestal is er slechts één aanvrager-id per programmeur. Een andere functie met betrekking tot de id van de aanvrager is dat de programmeur Adobe een openbaar certificaat moet verstrekken, aangezien de API-aanroep setRequestor verwacht dat gecodeerde gegevens worden verzonden en gebruikt om de programmeur te verifiëren in het Adobe Primetime-verificatiesysteem.

## Resource ID {#resource-id}

Een tekenreeks of MRSS-bron die een [Programmeur](#programmer) naar MVPD&#39;s. Het is overeengekomen tussen de programmeur en de MVPD&#39;s; De authentificatie van Adobe Primetime gaat identiteitskaart van het Middel door onaangeroerd over, zodat moet het voor alle MVPDs het zelfde zijn. Een programmeur kan veelvoudige middel IDs gebruiken zolang MVPDs zich van bewust is wat elke identiteitskaart vertegenwoordigt.

## SessionGUID {#sessionGUID}

Zie [Gebruikersnaam](#user-id).

## Token voor kortlevende media {#short-lived-token}

Dit token wordt gegenereerd door Adobe Primetime-verificatie wanneer het machtigingsproces voor een bepaalde gebruiker met succes is voltooid. Het token wordt doorgegeven aan de programmeur, die de Verificatietoken van Adobe Primetime-verificatietoken gebruikt op het token voor kortlevende media om de beveiliging van het machtigingsproces te controleren.

## Slim apparaat {#smart-device}

Een term die in de Adobe Primetime-verificatiedocumentatie wordt gebruikt om te verwijzen naar set-top boxes, spelconsoles en smart TV&#39;s. Dit zijn apparaten die voorzien van een netwerkmogelijkheden maar niet geschikt zijn om Web-pagina&#39;s terug te geven.

## SP{#sp}

Serviceverlener; dit verwijst gewoonlijk naar de *rol* van SP, gespeeld door de authentificatie van Adobe Primetime, handelend namens een Programmeur in een integratie met een [MVPD](#mvpd).

## Temperatuurcontrole {#temp-pass}

Een functie waarmee programmeurs tijdelijk gratis toegang kunnen bieden tot betaalinhoud. De toegang is per-Aanvrager, voor een programmeur-gespecificeerde periode.

## TTL {#ttl}

Tijd om te leven. Dit is de opgegeven tijdsduur dat een token geldig is.

## TVE {#tve}

Televisie overal.

## Gebruikersnaam {#user-id}

Hiermee wordt de gebruiker van de app van een programmeur op unieke wijze geïdentificeerd, maar wordt de gebruiker van de MVPD geregistreerd. Beschikbaar in verschillende formulieren voor verschillende gebruiksgevallen. Zie [Gebruikersidentiteitskaart van het begrip in het Overzicht van de Programmer](/help/authentication/programmer-overview.md#user-ids).

## Lijst van gewenste personen {#whitelist}

Een lijst met domeinen die als legitiem zijn aangewezen voor communicatie met Adobe Primetime-verificatie.

## XSTS-token {#xsts-token}

Een beveiligingstoken dat is uitgegeven door Microsoft for Xbox console-app-ontwikkeling, wordt gebruikt in Xbox/Adobe Primetime-verificatieintegratie.
