---
title: Gegevens van Primetime-verificatieservers integreren in Adobe Analytics
description: Gegevens van Primetime-verificatieservers integreren in Adobe Analytics
exl-id: c1f1f2a3-c98c-4aed-92ad-1f9bfd80b82b
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 4%

---

# Gegevens van de Primetime-verificatieserver integreren in Adobe Analytics

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

Klanten van Adobe Primetime-verificatie willen de gegevens op de server van Primetime-verificatie (Adobe Pass) in het Adobe Analytics-dashboard bekijken, zodat ze deze gemakkelijker kunnen gebruiken.

De gegevens zullen dienen om belangrijke metriek van TVE zoals authentificatieomzettingspercentages per MVPD, unieke gebruikers te volgen die op MVPD worden gebaseerd Gebruiker - identiteitskaart en meer.

Het is niet bedoeld om een clientimplementatie te vervangen als er al een bestaat, aangezien de gebruikersactiviteit bij afwezigheid van een bezoeker-id niet verder kan worden gevolgd dan de onderstaande specifieke gebeurtenissen. Als de klanten een bezoekersidentiteitskaart op de vraag van de pas verstrekken dan kunnen wij een ander type van de integratie van Analytics - echt - ontgrendelen die zich bij alle gebeurtenissen van de Controle met de bestaande klantengegevens kan aansluiten, meer details over dit nieuwe type van mogelijke integratie hier: &quot;[Experience Cloud-id gebruiken in Primetime-verificatie](/help/authentication/exp-cloud-id-authn.md)&quot;

## Inbegrepen cijfers {#metrics-included-int-authn-analyt}

| Gebeurtenis | Beschrijving |
|----------------------------|----------------------------------------------------------------------------------------------------------------------|
| AuthN opgevraagd | Aantal geïnitieerde verificatiestromen |
| AuthN in behandeling | Aantal met succes geproduceerde authentificatietokens (het negeren van al dan niet de cliënt werkelijk het verwierf) |
| AuthN OK | Aantal verificatietokens dat gebruikers hebben opgehaald |
| AuthZ aangevraagd | Aantal pogingen tot het verlenen van vergunningen |
| AuthZ OK | Aantal geslaagde toelatingen |
| AuthZ is mislukt | Aantal door de MVPD’s geweigerde vergunningen op toepassingsniveau |
| Aanvraag afspelen | Aantal gegenereerde korte mediatokens (die overeenkomen met het aantal afspeelverzoeken) |
| Aanmelding aangevraagd | Aantal geïnitieerde afmeldingsstromen |
| Afmelden voltooid | Aantal met succes voltooide logout-stromen |
| Afmelden mislukt | Aantal mislukte logout-stromen |
| Voorafgaande toestemming aangevraagd | Aantal geïnitieerde preautorisatiestromen |
| Voorkeursprocedure | Aantal geslaagde preautorisatiegebeurtenissen met de middelen die vooraf werden gemachtigd |
| Voorvergunning geweigerd | Aantal gebeurtenissen voorafgaand aan autorisatie met de middelen die vooraf werden geweigerd |
| Voorvertoning is mislukt | Aantal mislukte voorafgaande verificatie-gebeurtenissen |

| Adobe Analytics-naam | Beschrijving |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Kanaal | De aanvrager-id die wordt gebruikt voor het uitvoeren van de machtigingsaanvraag |
| MVPD | MVPD verantwoordelijk voor het toekennen van rechten aan de gebruiker |
| Proxy | De proxy-MVPD (die &quot;Direct&quot; zal zijn voor directe integratie) |
| Het type SDK | De SDK van de client die wordt gebruikt (Flash, HTML5, Android native, iOS, Clientless enz.) |
| SDK-versie | De versie van de Adobe Primetime-verificatieclient SDK |
| Resource ID | De feitelijke titel van de bron die bij het vergunningsverzoek is betrokken (geëxtraheerd uit de MRSS-lading als item/titel indien verstrekt) |
| AuthZ-fouttype | De reden voor fouten, zoals gemeld door Adobe Primetime-verificatie <br/> Hier zijn de meest voorkomende waarden <br/> **noAuthZ** = de MVPD antwoordde dat de gebruiker niet het kanaal in hun pakket heeft<br/> **netwerk** = wij konden MVPD niet bereiken (MVPD heeft een kwestie op het ogenblik van de vraag en antwoordde niet)<br/> **norefreshtoken** = dit is strikt voor implementaties OAuth en het zou kunnen resulteren als de gebruiker hun wachtwoord veranderde of MVPD het om één of andere reden ontkende. Het resulteert typisch in een nieuwe authentificatie<br/> **mismatch** = als het verzoek van een apparaat wordt gemaakt dat verschillend is dan het apparaat dat het authentificatietoken had. Dit kan het gevolg zijn als gebruikers proberen het systeem te bedriegen, maar de meeste hiervan deden zich voor in de context van onze oude JavaScript SDK waarin de apparaat-id het IP-adres als onderdeel van de berekening gebruikte. Als een gebruiker TVE thuis en op het werk zou controleren, zou deze fout worden geactiveerd en moesten deze opnieuw worden geverifieerd<br/> **ongeldig** = ongeldige aanvraag, ontbrekende of ongeldige parameters<br/>  **authzNone** = De programmeurs hebben de capaciteit om toestemmingen voor een specifieke channelxMVPD combinatie te ontkennen. Dit wordt geactiveerd door een back-end-API waartoe programmeurs toegang hebben<br/> **fraude** = het is een beschermingsmechanisme aan onze kant . Als de gebruiker vergunning ontbreekt en het dan een aantal tijden in een kort interval (seconden) opnieuw verzoekt ontkennen wij direct de vraag. Het gebeurt typisch wanneer een Programmer een insect in hun implementatie heeft die om vergunning constant vraagt als het ontbreekt. |
| Type token | Wanneer tokens door AuthZ allen en AuthN allen worden gecreeerd, moeten wij weten wat door een degradatiemaatregel wordt veroorzaakt.<br/> Het zijn:<br/> &quot;normal&quot; = het normale geval<br/> &quot;authnall&quot; = When AuthN All is enabled<br/> &quot;authzall&quot; = When AuthZ All is enabled<br/>  &quot;hba&quot; = Wanneer HBA is ingeschakeld |
| Apparaattype zonder clip | Het apparaatplatform (alternatief), momenteel gebruikt voor Clientless.<br/> De waarden kunnen zijn:<br/> N.v.t. - de gebeurtenis kwam niet voort uit een Clientless SDK<br/> Onbekend - Sinds de parameter deviceType van een **Clientloze API** is optioneel. Er zijn aanroepen die geen waarde bevatten.<br/> Een andere waarde die via de **Clientloze API**. Bijvoorbeeld xbox, appletv en roku. |
| MVPD-gebruikersnaam | Vervangt op cookie gebaseerde bezoeker-id |


## Details {#details-int-authn-analyt}

* De metriek wordt, gebeurtenis voor gebeurtenis, ingevoegd in het specifieke rapportpakket via de API voor het invoegen van gegevens van Adobe Analytics
* De invoeging wordt elke 30 minuten in een batch geplaatst en verzonden. Daarom moet het verslag worden voorzien van een tijdstempel
* Elke klant zal één of veelvoudige rapportseries hebben. Eén aanvrager-id (kanaal) wijst slechts aan één rapportsuite toe. Meerdere verzoek-id&#39;s kunnen aan slechts één rapportsuite worden toegewezen.
* Historische gegevens kunnen worden verstrekt, maar er moet speciale aandacht worden besteed aan verkeersproblemen/prestatieproblemen.
* De unieke bezoekersvariabele wordt ingesteld op de MVPD-gebruikersnaam
* Het in kaart brengen van gebeurtenissen en eVars is niet configureerbaar.


## SLA {#sla-int-authn-serv-anal}

Aangezien het geen kritieke component is, is er geen SLA garantie voor de integratie.

## Configuratie van rapportsuite {#report-suite-config}

Het rapport moet een tijdstempel hebben omdat de gebeurtenissen batchgewijs worden verzonden.

### Gebeurtenissen {#report-suite-config-events}


>[!NOTE]
>Alles moet worden ingesteld met:
>
>* Teller (geen subrelaties)


| Gebeurtenis | Adobe Analytics, gebeurtenis |
|---------------------------------------|-----------------------|
| AuthN opgevraagd | event1 |
| AuthN in behandeling | event2 |
| AuthN OK | event3 |
| AuthZ aangevraagd | event4 |
| AuthZ OK | event5 |
| AuthZ is mislukt | event6 |
| Aanvraag afspelen | event7 |
| AuthN mislukt | event8 |
| Clientless AuthN Token Request OK | event9 |
| Aanvraag voor token voor client-less AuthN is mislukt | event10 |
| Aanvraag afspelen is mislukt | event11 |
| Aanvraag tot aanmelding | event12 |
| Afmelden voltooid | event13 |
| Afmelden mislukt | event14 |
| Preflight-aanvraag | event15 |
| Preflight is mislukt | event16 |
| Preflight toegekend | event17 |
| Preflight geweigerd | event18 |


### eVars {#evars}


>[!NOTE]
>Alles moet worden ingesteld met:
>
>* Toewijzing: Recentste (laatste)
>* Verlopen na: Actief
>* Type: Tekstreeks


| Eigenschap | eVar |
|-----------------------------------|--------------------------------|
| Kanaal | eVar1 |
| MVPD | eVar2 |
| Proxy | eVar3 |
| Het type SDK | eVar4 |
| SDK-versie | eVar5 |
| Resource ID | eVar6 |
| AuthZ-fouttype | eVar7 |
| Type token | eVar8 |
| Apparaattype zonder clip | eVar9 |
| MVPD-gebruikersnaam | bezoekerID (automatisch gedaan) |
| MVPD-gebruikersnaam | eVar10 |
| Apparaattype | eVar11 |
| Besturingssysteem | eVar12 |
| Primair hardwaretype | eVar13 |
| TTL | eVar14 |
| Type verificatie | eVar15 |
| Versie van serverarchitectuur | eVar16 |
| Externe verificatieprovider | eVar17 |
| Latentie | eVar18 |
| Bezoeker-id | eVar19 |
| SSO-mechanisme | eVar20 |
| Apparaatmodel | eVar21 |
| Apparaatversie | eVar22 |
| Hardware-model apparaat | eVar23 |
| Hardware-leverancier van apparaat | eVar24 |
| Hardware-fabrikant apparaat | eVar25 |
| Hardware-versie van apparaat | eVar26 |
| Besturingssysteemnaam apparaat | eVar27 |
| Apparaatbesturingssysteem | eVar28 |
| Leverancier van besturingssystemen van apparaat | eVar29 |
| Versie van besturingssysteem van apparaat | eVar30 |
| Naam apparaatbrowser | eVar31 |
| Leverancier apparaatbrowser | eVar32 |
| Versie apparaatbrowser | eVar33 |
| Genormaliseerd apparaattype zonder clip | eVar34 |

## Prijzen {#pricing}

Neem contact op met uw TAM voor meer informatie.
