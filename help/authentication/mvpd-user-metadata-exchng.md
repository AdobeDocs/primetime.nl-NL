---
title: MVPD-uitwisseling van metagegevens van gebruikers
description: MVPD-uitwisseling van metagegevens van gebruikers
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---


# MVPD-uitwisseling van metagegevens van gebruikers

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding {#intro-user-metadata-exchange}

MVPDs handhaaft gebruiker-specifieke meta-gegevens over hun klanten die in sommige gevallen met Programmers wordt gedeeld. Het doel van Adobe Primetime-authenticatie is een uitwisseling van deze &quot;metagegevens van gebruikers&quot; mogelijk te maken, maar geen regels voor de uitwisseling af te dwingen. De uitwisselingsregels zijn voor MVPDs om met hun partners van de Programmer uit te werken.

De volgende gegevenstypen voor gebruikers zijn momenteel beschikbaar voor uitwisseling:

* Postcode
* Maximale classificatie (VChip of MPAA)
* Gebruikersnaam
* Huishoudelijke ID
* Kanaal-id

Gebruikend deze eigenschap, kunnen MVPDs en Programmers speciale gebruiksgevallen zoals oudercontrole uitvoeren. Bijvoorbeeld, kan een MVPD ouderlijke classificatiegegevens tot een Programmer overgaan, die dan die gegevens gebruikt om beschikbare het bekijken keuzen voor een gebruiker te filtreren.

Belangrijke punten van metagegevens van gebruiker:

* MVPD gaat gebruikersmeta-gegevens tot de toepassing van de Programmer tijdens de authentificatie en vergunningsstromen over
* Adobe Primetime-verificatie slaat de metagegevenswaarden op in de tokens AuthN en AuthZ
* Adobe Primetime-verificatie kan waarden normaliseren voor MVPD&#39;s die gebruikersmetagegevens in verschillende indelingen bieden
* Sommige parameters kunnen worden gecodeerd met behulp van de sleutel van de programmeur
* Adobe stelt specifieke waarden beschikbaar via een configuratiewijziging

>[!NOTE]
>
>De meta-gegevens van de gebruiker is een uitbreiding op de statische meta-gegevens (het teken van de Authentificatie TTL, het teken van de Token van de Toestemming TTL, en identiteitskaart van het Apparaat) eerder beschikbaar in de authentificatie van Adobe Primetime.

## Voorbeelden {#example-mvpd-user-metadata-exch}

### Ouderlijk toezicht {#example-parental-control}

In dit voorbeeld wordt de uitwisseling van het volgende getoond:

* [Programmeren naar MVPD Metadata Exchange](#progr-mvpd-metadata-exch)

* [MVPD aan de Stroom van de Uitwisseling van Metagegevens van de Programmer](#mvpd-progr-exchange-flow)

### Programmeren naar MVPD Metadata Exchange {#progr-mvpd-metadata-exch}

Momenteel steunen de programmeur API, de authentificatie van Adobe Primetime, en de Auteurs MVPD allen slechts kanaal-vlakke vergunning. Het kanaal wordt als onbewerkte teksttekenreeks opgegeven in de API-aanroep getAuthorization() van de programmeur. Deze tekenreeks wordt volledig doorgegeven aan de autoriserende backend van de MVPD:

Van de app of de plaats van de Programmer, kiest de gebruiker XACML geschikt MVPD (in dit voorbeeld, &quot;TNT&quot;). Voor informatie over XACML, zie [eXtensible Access Control Markup Language](https://en.wikipedia.org/wiki/XACML){target=_blank}.
De toepassing van de Programmer vormt een verzoek AuthZ dat de middel en zijn meta-gegevens omvat.  Dit voorbeeld bevat een MPAA-classificatie van &quot;pg&quot; in het mediakarakter van het kanaalelement:

```XML
var resource = '<rss version="2.0" xmlns:media="http://video.search.yahoo.com/mrss/">
                    <channel> 
                        <title>TNT</title> 
                        <media:rating scheme="urn:mpaa">pg</media:rating>
                    </channel>
                </rss>';
getAuthorization(resource);
```

De authentificatie van Adobe Primetime steunt eigenlijk meer korrelige vergunning, tot het activaniveau, wanneer gesteund door zowel MVPD als programmeur. De bron en de metagegevens zijn ondoorzichtig voor Adobe; de bedoeling is een standaardformaat voor het specificeren van middelidentiteitskaart en meta-gegevens op een genormaliseerde manier te vestigen, om middel IDs naar verschillende MVPDs te verzenden.

>[!NOTE]
>
>Als de gebruiker een kanaal-slechts geschikt MVPD kiest, dan haalt de authentificatie van Adobe Primetime SLECHTS de kanaaltitel (&quot;TNT&quot;in het bovenstaande voorbeeld) en gaat slechts de titel tot MVPD over.

### MVPD aan de Stroom van de Uitwisseling van Metagegevens van de Programmer {#mvpd-progr-exchange-flow}

Bij Adobe Primetime-verificatie worden de volgende veronderstellingen gehanteerd:

* MVPD verzendt de maximumclassificatie als deel van de reactie SAML
* Deze informatie wordt opgeslagen als onderdeel van het verificatietoken
* Een API wordt geleverd door Adobe Primetime-verificatie, zodat programmeurs deze informatie kunnen ophalen
* Programmeurs implementeren deze functie op hun site of in hun app (bijvoorbeeld om video&#39;s te verbergen die de maximale score voor de gebruiker overschrijden)

```XML
<saml:Assertion ID="pfxec5f92e0-8589-3fc3-c708-f4fb8e2fad59"
                 IssueInstant="2010-07-20T10:05:41Z" Version="2.0"
                 xmlns:xs="http://www.w3.org/2001/XMLSchema"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <saml:AttributeStatement>
        <saml:Attribute
                Name="MaxTVRating"
                NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
            <saml:AttributeValue xsi:type="xs:string">tv-ma</saml:AttributeValue>
        </saml:Attribute>
        <saml:Attribute
                Name="MaxMovieRating"
                NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:basic">
            <saml:AttributeValue xsi:type="xs:string">nc-17</saml:AttributeValue>
        </saml:Attribute>
    </saml:AttributeStatement>
</saml:Assertion>
```

### Notities {#notes-mvpd-progr-metadata-exch-flow}

**Bronnormalisatie en -validatie.** Middel IDs kan als gewone koord of een koord worden overgegaan MRSS. Een programmeur kan besluiten of het duidelijke koordformaat of MRSS te gebruiken, maar zal een voorafgaande overeenkomst met MVPD nodig hebben zodat MVPD weet hoe te om dat middel te behandelen.

**Bron-id en metagegevensspecificatie.** Adobe Primetime-verificatie gebruikt de RSS-standaard met de Media RSS-extensie om een bron en de bijbehorende metagegevens op te geven. In combinatie met de Media RSS-extensie biedt Adobe Primetime-verificatie ondersteuning voor een groot aantal verschillende metagegevens, zoals ouderlijk toezicht (via `<media:rating>`) of geolocatie (`<media:location>`).

De authentificatie van Adobe Primetime kan transparante omzetting van het koord van het erfeniskanaal aan het overeenkomstige middel RSS voor MVPDs ook steunen die RSS vereisen. In de andere richting, steunt de authentificatie van Adobe Primetime omzetting van RSS+MRSS aan gewone kanaaltitel, voor kanaal-slechts MVPDs.

**Adobe Primetime-verificatie zorgt voor volledige achterwaartse compatibiliteit met bestaande integratie.** Namelijk voor Programmeurs die kanaal-vlakke authentificatie gebruiken, zorgt de authentificatie van Adobe Primetime ervoor om kanaalidentiteitskaart in het noodzakelijke formaat te verpakken alvorens het naar MVPD te verzenden die dat formaat begrijpt. Het omgekeerde geldt ook: als een programmeur al zijn middelen in een nieuw formaat specificeert, vertaalt de authentificatie van Adobe Primetime het nieuwe formaat aan een eenvoudig kanaalkoord als het machtigen tegen MVPD die slechts de vergunning van het kanaalniveau doet.

## Gebruiksscenario&#39;s voor metagegevens van gebruiker {#user-metadata-use-cases}

De gevallen van het gebruik zijn voortdurend veranderend en uitbreidend aangezien meer MVPDs wettelijke regelingen en toevoegt functionaliteit maakt. Hieronder ziet u voorbeelden van gebruikersmetagegevens.

* [MVPD-gebruikersnaam](#mvpd-user-id)
* [Huishoudelijke ID](#household-user-id)
* [Postcode](#zip-code)
* [Max. score (ouderlijk toezicht)](#max-rating-parental-control)
* [Kanaal lineup](#channel-line-up)

### MVPD-gebruikersnaam {#mvpd-user-id}

* Zoals verstrekt door het MVPD
* Niet de daadwerkelijke login informatie van de gebruiker, aangezien het door MVPD wordt gehakt
* Kan worden gebruikt om problemen aan te geven met of voor specifieke gebruikers
* Gecodeerd
* MVPD-ondersteuning: Alle MVPD&#39;s

### Huishoudelijke gebruikersnaam {#household-user-id}

* Staat goede metrische informatie toe
* Gecodeerd
* MVPD-ondersteuning: Sommige MVPD&#39;s

### Postcode {#zip-code}

* De postcode voor facturering van de gebruiker
* Primair gebruikt om de regels voor het blokkeren van sportevenementen af te dwingen
* Kan worden geleverd met de AuthZ-respons voor snelle updates
* MVPD-ondersteuning: Sommige MVPD&#39;s

### Max. score (ouderlijk toezicht) {#max-rating-parental-control}

* Aanvankelijk AuthN, plus AuthZ verfrist zich
* Inhoud uit de gebruikersinterface filteren
* MPAA- of VChip-ratings
* MVPD-ondersteuning: Sommige MVPD&#39;s

### Kanaal lineup {#channel-line-up}

* MVPDs kan een lijst van kanalen verstrekken die de gebruiker gerechtigd is te bekijken
* Maakt snel tekenen in de gebruikersinterface mogelijk
* De specificatie OLCA staat voor dit als AttributeStatement in de reactie van AuthN toe
* Ondersteuning voor MVPD&#39;s: Sommige MVPD&#39;s

<!--
>[!RELATEDINFORMATION]
>
>* [Proxy MVPD Web Service](/help/authentication/proxy-mvpd-webserv.md)
>* [Content Metadata Exhange](/help/authentication/mvpd-content-metadata-exchange.md)
>* [OLCA AuthN / AuthZ Specification](https://www.cablelabs.com/specifications/CL-SP-AUTH1.0-I04-120621.pdf){target=_blank}
>* [User Metadata (Programmer Integration Guide)](/help/authentication/user-metadata-feature.md)
-->
