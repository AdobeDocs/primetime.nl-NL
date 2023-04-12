---
title: Overzicht van Entitlement Service-controle
description: Overzicht van Entitlement Service-controle
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Overzicht van Entitlement Service-controle {#entitlement-service-monitoring-overview}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding {#introduction}

TVE-sites en -toepassingen moeten 24/7 beschikbaar zijn, dus klanten hebben realtime inzicht nodig in machtigingsgebeurtenissen om problemen zo snel mogelijk te kunnen detecteren en corrigeren. Zij moeten ook maandgegevens analyseren om te bepalen welke platforms het grootste deel van het verkeer leveren, en welke platforms een slechte implementatie en slechte omrekeningskoersen zouden kunnen hebben.

De Controle van de Dienst van het recht (ESM) verstrekt Programmers en MVPDs van een gegevensvoer die zicht in real time in hun Authentificatie en de gebeurtenissen van de Vergunning aanbiedt. De gegevens worden verzameld bij de Adobe Primetime-verificatiesystemen en via een RESTful-API verstrekt.  Klanten kunnen de gegevens direct of vanuit hun eigen aangepaste, operationele dashboards gebruiken.

De kernelementen van het ESM-systeem zijn de meetwaarden en dimensies ervan. ESM produceert rapporten die samengevoegde metriek volgens de afmetingsselectie bevatten. Aangezien de gebeurtenissen van Adobe Pass PST timezone het programma worden geopend, zijn de rapporten ESM ook beschikbaar in timezone PST. 

De ESM API is niet algemeen beschikbaar.  Neem contact op met uw Adobe-vertegenwoordiger voor vragen over beschikbaarheid.

## ESM voor programmeurs {#esm-for-programmers}

### Programmeurs kunnen de volgende meetgegevens controleren: {#programmers-monitor-metrics}


| *Metrische naam* | *Beschrijving* |
|-------------------------|--------------------------|
| authnPogingen | Aantal geïnitieerde verificatiestromen |
| gelukt | Aantal verificatietokens dat is verkregen door clients |
| in behandeling | Aantal met succes geproduceerde authentificatietokens (het negeren van al dan niet de cliënt werkelijk het verwierf) |
| authn-failed | Aantal mislukte verificatie uitgevoerd via een extern systeem. |
| clientless-tokens | Aantal Clientless tokens dat is uitgegeven |
| clientless-failure | Aantal mislukte pogingen om tokens van de Clientless API te ontvangen |
| autorisatiepogingen | Aantal pogingen tot het verlenen van vergunningen |
| authz succesvol | Aantal geslaagde toelatingen |
| authz-failed | Aantal door de MVPD’s geweigerde vergunningen op toepassingsniveau |
| afgekeurd | Aantal pogingen van vergunningen die als kwaadwillig door de Leverancier van de Dienst van Adobe worden beschouwd en als resultaat van een de aanvalspreventie van Dos worden verworpen |
| authz-latentie | Totaal aantal milliseconden besteed aan het eindpunt van MVPD |
| media-tokens | Aantal gegenereerde korte mediatokens (die overeenkomen met het aantal afspeelverzoeken) |
| unieke accounts | Aantal unieke gebruikers die machtigingsacties (AuthN / AuthZ) in het geselecteerde tijdinterval hebben uitgevoerd. (Deze metrische waarde geeft alleen aan of er om dagelijkse waarden wordt gevraagd.) </br> Dit wordt berekend voor elk individueel Centrum van Gegevens. Wanneer de afmeting &quot;dc&quot;niet wordt gevraagd, zal metrisch niet worden getoond. |
| unieke sessies | Aantal unieke zittingen die de vraag van de authentificatiestroom aan de de authentificatieservice van Adobe Primetime binnen het geselecteerde tijdinterval uitvoerden. (Deze metrische waarde geeft alleen aan of er om dagelijkse waarden wordt gevraagd.) </br> Dit wordt berekend voor elk individueel Centrum van Gegevens. Wanneer de afmeting &quot;dc&quot;niet wordt gevraagd, zal metrisch niet worden getoond. |
| aantal | Een eenvoudige teller die in de gebeurtenis-georiënteerde rapporten wordt gebruikt |

</br>

### Programmeurs kunnen de hierboven vermelde metriek door de volgende afmetingen filtreren: {#progr-filter-metrics}


| *Dimension-naam* | *Beschrijving* |
|---|---|
| jaar | Jaar met 4 cijfers |
| maand | De maand van het jaar (1-12) |
| dag | Dag van de maand (1-31) |
| uur | Het uur van de dag |
| minuut | De minuut van het uur |
| mediabedrijf | Het mediabedrijf dat eigenaar is van de website die het machtigingsproces voor de gebruiker heeft gestart |
| dc | (Gegevenscentrum) Het thuisgebied waar het verzoek is ontvangen. |
| proxy | De proxy-MVPD (die &quot;Direct&quot; zal zijn voor directe integratie) |
| mvpd | MVPD verantwoordelijk voor het toekennen van rechten aan de gebruiker |
| aanvrager-id | De aanvrager-id die wordt gebruikt voor het uitvoeren van de machtigingsaanvraag |
| kanaal | De kanaalwebsite, die uit het middelgebied wordt gehaald (die uit de nuttige lading MRSS als kanaal/titel indien verstrekt wordt gehaald, of aan de middelwaarde in kaart gebracht als het niet in formaat RSS is). |
| resource-id | De feitelijke titel van de bron die bij het vergunningsverzoek is betrokken (geëxtraheerd uit de MRSS-lading als item/titel indien verstrekt) |
| apparaat | Het platform van het apparaat (PC, mobiel, console, enz.) |
| eindigen | De externe verificatieprovider wanneer de verificatiestroom wordt uitgevoerd via een extern systeem. </br> De waarden kunnen zijn: </br> - N.v.t. - de authentificatie werd verstrekt door authentificatie Primetime </br> - Apple - het externe systeem dat de verificatie heeft verstrekt, is Apple |
| os-family | Besturingssysteem dat op het apparaat wordt uitgevoerd |
| browser-familie | Gebruikersagent gebruikt voor toegang tot Adobe Primetime-verificatie |
| cdt | Het apparaatplatform (alternatief), momenteel gebruikt voor Clientless. </br>  De waarden kunnen zijn: </br> - N.v.t. - de gebeurtenis kwam niet voort uit een Clientless SDK </br> - Onbekend - Aangezien de parameter deviceType van een Clientless API optioneel is, zijn er aanroepen die geen waarde bevatten. </br> - elke andere waarde die via de Clientless API is verzonden, bijvoorbeeld xbox, appletv, roku enz. </br> |
| platformversie | De versie van de Clientless SDK |
| van het type os | Besturingssysteem dat op het apparaat wordt uitgevoerd, alternatief (momenteel niet gebruikt) |
| browserversie | Versie van gebruikersagent |
| sdk-type | De SDK van de client die wordt gebruikt (Flash, HTML5, Android native, iOS, Clientless enz.) |
| sdk-versie | De versie van de Adobe Primetime-verificatieclient SDK |
| event | De naam van de Adobe Primetime-verificatiegebeurtenis |
| reden | De reden voor fouten, zoals gemeld door Adobe Primetime-verificatie |
| van het type sso | Het onderliggende SSO-mechanisme: platform/passief/adobe. Geeft aan dat het verificatietoken is uitgegeven door AuthN opnieuw te gebruiken in een andere toepassing |

## ESM voor MVPD&#39;s {#esm-for-mvpds}

### MVPDs kan de volgende metriek controleren:

| *Metrische naam* | *Beschrijving* |
|---|---|
| authnPogingen | Aantal geïnitieerde verificatiestromen |
| gelukt | Aantal verificatietokens dat is verkregen door clients |
| in behandeling | Aantal met succes geproduceerde authentificatietokens (het negeren van al dan niet de cliënt werkelijk het verwierf) |
| authn-failed | Aantal mislukte verificatie uitgevoerd via een extern systeem. |
| autorisatiepogingen | Aantal pogingen tot het verlenen van vergunningen |
| authz succesvol | Aantal geslaagde toelatingen |
| authz-failed | Aantal door de MVPD’s geweigerde vergunningen op toepassingsniveau |
| afgekeurd | Aantal pogingen van vergunningen die als kwaadwillig door de Leverancier van de Dienst van Adobe worden beschouwd en als resultaat van een de aanvalspreventie van Dos worden verworpen |
| authz-latentie | Totaal aantal milliseconden besteed aan het eindpunt van MVPD |

### MVPD&#39;s kunnen de hierboven vermelde metingen filteren op de volgende afmetingen:

| *Dimension-naam* | *Beschrijving* |
|---|---|
| jaar | Jaar met 4 cijfers |
| maand | De maand van het jaar (1-12) |
| dag | Dag van de maand (1-31) |
| uur | Het uur van de dag |
| minuut | De minuut van het uur |
| aanvrager-id | De aanvrager-id die wordt gebruikt voor het uitvoeren van de machtigingsaanvraag |
| eindigen | De externe verificatieprovider wanneer de verificatiestroom wordt uitgevoerd via een extern systeem. </br> De waarden kunnen zijn: </br> - N.v.t. - de authentificatie werd verstrekt door authentificatie Primetime </br> - Apple - het externe systeem dat de verificatie heeft verstrekt, is Apple |
| cdt | Het apparaatplatform (alternatief), momenteel gebruikt voor Clientless. </br>  De waarden kunnen zijn: </br> - N.v.t. - de gebeurtenis kwam niet voort uit een Clientless SDK </br> - Onbekend - Aangezien de parameter deviceType van een Clientless API optioneel is, zijn er aanroepen die geen waarde bevatten. </br> - elke andere waarde die via de Clientless API is verzonden, bijvoorbeeld xbox, appletv, roku enz. </br> |
| sdk-type | De SDK van de client die wordt gebruikt (Flash, HTML5, Android native, iOS, Clientless enz.) |


## Gevallen gebruiken {#use-cases}

U kunt de ESM-gegevens gebruiken voor de volgende gebruiksgevallen:

- **Toezicht** - Ops of controleteams kunnen een dashboard of grafiek maken die elke minuut de API aanroept. Gebruikend de getoonde informatie kunnen zij een probleem (met authentificatie Primetime, of met MVPD) ontdekken het minuut het verschijnt.  

- **Foutopsporing/Kwaliteitstests** - Omdat gegevens ook worden uitgesplitst naar platform, apparaat, browser en besturingssysteem, kan het analyseren van gebruikspatronen problemen op specifieke combinaties (bijvoorbeeld Safari op OSX) opsporen.  

- **Analyse** - De verstrekte gegevens kunnen worden gebruikt ter aanvulling/controle van de gegevens aan de clientzijde die worden verzameld via Adobe Analytics of een ander analysehulpmiddel.

<!--
## Related Information {#related-information}

- [ESM API](/help/authentication/entitlement-service-monitoring-api.md)
- [Degradation API Overview](/help/authentication/degradation-api-overview.md)
- [Server-side Metrics](/help/authentication/understanding-serverside-metrics.md)
-->