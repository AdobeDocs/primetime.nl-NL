---
title: MVPD-integratiefuncties
description: MVPD-integratiefuncties
exl-id: fcd65940-9a86-49b2-9d52-9031fb763338
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 2%

---

# MVPD-integratiefuncties

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Overzicht {#mvpd-int-features-overview}

Adobe Primetime-verificatie biedt ondersteuning voor de nieuwe standaarden voor tv overal. Het voldoet aan de **CableLabs OLCA-specificatie (Online Content Access)**, die technische vereisten en architectuur voor de levering van video aan een klant van de TV van het Betaal van online bronnen verstrekt. Adobe nam in juni 2011 deel aan het gezamenlijke CableLabs-interoptestproject en stemde in met het testproces voor een Service Provider-implementatie.  Adobe is ook actief lid van de **OATC (Open Authentication Technical Consortium)** en neemt als onderdeel van die instantie deel aan diverse specificatieontwerpen van de subcomités.

Nadat u Primetime-verificatie hebt beschreven, voldoet Primetime-verificatie aan de OLATC-Adobe. Het is ook belangrijk om te weten dat Primetime-verificatie in feite &quot;protocolagnostisch&quot; is.  Maar in dit stadium van het TVE-tijdperk is Primetime-verificatie zeker gericht op de OLCA-standaarden.  De normen bepalen momenteel overeengekomen manieren voor de verschillende spelers TVE (Programmers, MVPDs, en Dienstverleners) om de eigenschappen van TVE uit te voeren. Veel van deze functies worden weergegeven in de onderstaande tabellen, met koppelingen naar verwante pagina&#39;s die details en voorbeelden geven van hoe u de functies kunt implementeren.

De informatie in de lijsten is bedoeld om het proces van de authentificatieintegratie van Primetime naar verenigbare functionaliteit over alle integratie te drijven MVPD. De prioritaire kolom rangschikt de eigenschappen in A, B, en C:

* A - Dit zijn &quot;must&quot;-kenmerken voor de eerste uitrol van een integratie.
* B - Dit zijn belangrijke verbeteringen aan de eerste integratie, die na de eerste uitrol moeten worden toegevoegd.
* C - Dit zijn verdere verbeteringen van de integratie die kunnen worden geïmplementeerd na de B-vereisten.


## 1. Functionele basisfuncties {#core-func-features}


| Nee. | Functie | Beschrijving | Prioriteit | Notities |
|------|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.1 | [Door programmeur geïnitieerde aanmelding](/help/authentication/authn-oauth2-protocol.md) | De kijker selecteert MVPD en stelt de authentificatiestroom (AuthN) van de website of de toepassing van het merk van de Programmer in werking. | A+ |  |
| 1.2 | [Autorisatie op basis van kanalen](/help/authentication/authz-usecase.md) | Zodra voor authentiek verklaard, kan de vergunning (AuthZ) op de achtergrond voorkomen, met het overgaan van slechts een netwerkkanaalherkenningsteken, en een gebruikersidentificatie, aan MVPD. | A+ |  |
| 1.3 | Persistentie van gebruikersnaam | De MVPD verstrekt een verduisterde, blijvende GebruikerID. | A |  |
| 1.4 | [Support voor Single Sign-On](/help/authentication/sso-support.md) | De viewer meldt zich aan bij de MVPD op de site van één merk en kan vervolgens naar een ander merk gaan en niet worden gevraagd zich opnieuw aan te melden. De sessie AuthN wordt gedeeld tussen de merken. SSO-ondersteuning is zowel voor websites als voor mobiele toepassingen/apparaattoepassingen.  Voor MVPDs, vereist het het terugkeren van of een Gebruiker - identiteitskaart of één of ander ander ander gebruikerstoken die voor AuthZ over merken kan worden gebruikt. | A |  |
| 1.5 | Apparaatgeoptimaliseerde gebruikerservaring voor aanmelding (UX) | MVPD steunt resizing het login scherm zodat het de afmetingen van het apparaat past de mening gebruikt. | A |  |
| 1.6 | Standaardlogo voor MVPD-kiezer | De MVPD biedt een URL naar een standaardlogo met de juiste afmetingen (112 x 33 pixels). | A | Het logo moet worden gehost door de MVPD en in de cache worden opgeslagen door de CDN. |
| 1.7 | [Scoping serviceprovider](/help/authentication/serv-provider-scoping.md) | MVPD steunt het overgaan van merkherkenningsteken (de waarde van de Aanvrager) in het verzoek AuthN. | A- | Dit laat een dienstverlener-specifieke login ervaring toe. |
| 1.8 | [Meerkanaalautorisatie](/help/authentication/mvpd-preflight-authz.md#preflight-multich-authz) | MVPD steunt een Programmer die veelvoudige kanalen in één enkel vergunningsverzoek verzendt. | B+ |  |
| 1.9 | Verificatie op basis van iFrame of &#39;JS Pop-up&#39; | De programmeur kan de login stroom in een iFrame of pop-up ervaring in plaats van HTTP redirect integreren. | B |  |
| 1.10 | [Door programmeur geïnitieerde afmelding](/help/authentication/usecase-mvpd-logout.md) | De kijker heeft een voor authentiek verklaarde zitting zowel op de Plaats van de Programmer of App als met MVPD. De kijker kan een gefederaliseerde logout van de plaats van de Programmer in werking stellen, en logout ontruimt ook de zitting op het MVPD portaal. | B | Zorgt ervoor dat gedeelde computers beter worden beschermd tegen misbruik vanuit het perspectief van de programmeur. |
| 1.11 | [Aangepaste foutmelding voor autorisatie](/help/authentication/error-reporting.md) | MVPD gaat zijn eigen koord van de douanefout over, dat voor de gefedereerde Plaats of App van de Programmer aan vertoning aan de gebruiker aangewezen is. | B | Laat omhoog-verkoopscenario&#39;s toe |
| 1.12 | **Gebruikersmetagegevens over verificatiereactie** | De reactie MVPD AuthN kan gebruikersmeta-gegevens omvatten die als wenk voor verpersoonlijking van de ervaring van de gebruiker tijdens de machtigingsstroom dienst doen. Deze vereiste maakt ouderlijke controlehints mogelijk van de MVPD naar de programmeur. | B- |  |
| 1.13 | MVPD-In werking gestelde Authentificatie | De kijker voltooit een succesvolle zitting AuthN op het MVPD portaal, en navigeert dan aan de plaats van TVE van de Programmer. De gebruiker wordt niet veroorzaakt voor de plukker MVPD en automatisch voor authentiek verklaard. | B- |  |
| 1.14 | Gebruikersnamen | De MVPD-gebruikers-id moet in twee vormen worden gebruikt: de ene is bestemd voor programmeurs en de andere voor fraude voor de hele Adobe.  Dit staat Adobe toe om de programmeur-scoped MVPD Gebruiker te delen - identiteitskaart zonder verdere encryptie/obfuscatie. | C |  |
| 1.15 | Autorisatie op basis van bedrijfsmiddelen | Zodra AuthN wordt voltooid, kan AuthZ op de achtergrond gebeuren, door gestructureerde gegevens over te gaan die netwerk, tonen, activa, ouderlijke controle classificatie, en meer kunnen omvatten zoals nodig. Dit laat ouderlijke controles op elke vraag AuthZ van de Programmer aan MVPD toe. | C |  |
| 1.16 | MVPD-Geopende Logout | De viewer heeft een geverifieerde sessie op de site of in de app van de programmeur en met de MVPD. De kijker kan een gefederaliseerde logout van de plaats in werking stellen MVPD die ook de zitting op alle gefederaliseerde plaatsen van de Programmer ontruimt. | C |  |
| 1.17 | Vergunningsverplichtingen | MVPD verstrekt extra voorwaarden in de reactie AuthZ, zoals registreren, of een verfrist maximum ouderlijke controle classificatie (OLCA). | C |  |
| 1.18 | Context IP-adres | MVPD vereist uitdrukkelijk het IP adres overgaan. Voor AuthZ, waar de vraag server-kant is, geeft dit de fraude die MVPD informatie over waar de gebruiker uit op de vraag AuthZ komt. | C |  |
| 1.19 | Token Persistence Time-to-live (TTL) Waarde dynamisch gedefinieerd | MVPD kan TTL van het teken van de authentificatie Primetime dynamisch door eigenschappen in de reactie plaatsen, zodat Adobe uit de lijn voor de veranderingen van TTL is. | C- |  |
| 1.20 | Apparaattype | MVPD steunt het overgaan van het apparatentype in het verzoek AuthN of AuthZ. Dit bezit informeert MVPD over de aard van het apparaat waar de inhoud zal worden verbruikt, zodat konden zij TTL van het teken AuthN of AuthZ aanpassen om met hun eigen veiligheidsoverwegingen voor het apparaat in overeenstemming te zijn. | C- | Dit is nuttig voor het clientless platform, waar het moeilijk kan zijn om elk apparatentype als config plaatsend op de kant van de authentificatie van Primetime bloot te stellen. |



## 2. Operationele functies {#operational-features}

| Nee | Functie | Beschrijving | Prioriteit | Notities |
|-----|----------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|-------|
| 2.1 | 24/7 Up-time | Een MVPD-overeenkomst om 24 uur per dag en 7 dagen per week naar een hoger plan te streven en tegen dat doel in de loop der tijd te meten. | A |  |
| 2.2 | Referenties testen voor elke programmeur | MVPD verstrekt afzonderlijke testrekeningen voor elke Programmer. | A |  |
| 2.3 | Certificaatvervaldatum en verlengingsschema | Een MVPD-gedocumenteerd plan met een programma om de certificaten van SAML te verzekeren is bijgewerkt. | A- |  |
| 2.4 | Gemiddelde latentie onder 250 ms/respons | Een MVPD-overeenkomst om te streven naar een lage latentie en om tegen die vertraging te meten. | A- |  |
| 2.5 | Logo van eigen MVPD-kiezer hosten | MVPD moet hun eigen embleem ontvangen en het zou door CDN caching moeten worden beschermd. | B |  |
| 2.6 | Ondersteuningsschaalingsplan | Een MVPD-gedocumenteerd plan voor escalatie dat wordt bijgewerkt en minstens driemaandelijks herzien. | A |  |
| 2.7 | Uitvalbeveiligingsplan | Een MVPD-co-plan met Adobe over afbraakmaatregelen die zo nodig algemeen kunnen worden gebruikt. | B |  |
| 2.8 | Afzonderlijke eindpunten voor staging en productie behouden | Een integratietest MVPD die hostfile geen spoofing vereist om de het opvoeren integratie te testen. | B |  |
| 2.9 | Aanvullend QA-eindpunt | MVPD handhaaft een extra integratie QA IdP voor gezamenlijke nieuwe eigenschapontwikkeling.  Als dit wordt ondersteund, is het minder waarschijnlijk dat we speciale UAT-aanvragen voor cert-tests voor App Store nodig hebben. | C |  |





## 3. Verificatieervaring {#authn-exp-features}


| Nee | Functie | Beschrijving | Prioriteit | Notities |
|-----|----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| 3.1 | Verificatieomzetting over minimumverwachting | De MVPD garandeert een minimale conversiegraad om goed te functioneren (5%) en redelijk te zijn (30%). | A |  |
| 3.2 | Inline wachtwoordherstel | MVPD verstrekt een middel om wachtwoorden aan de gefedereerde stroom terug te krijgen AuthN. | A |  |
| 3.3 | Inline-accountregistratie | MVPD verstrekt een middel om een nieuwe rekening tot stand te brengen gealigneerd AuthN stroom. | A |  |
| 3.4 | Inline Help/ondersteuning | MVPD verstrekt een middel om hulp tijdens de federated stroom te verlenen AuthN. | A |  |
| 3.5 | Op modem gebaseerde interne verificatie | MVPD verklaart automatisch een apparaat voor authentiek wanneer het op het lokale netwerk van een geregistreerd model (ISP MVPD slechts) is. | B | Dit is lagere prioriteit omdat het een optimalisering is die velen nog niet kunnen steunen en sommige uitdagingen voor fraude matiging en ouderlijke controles introduceert |
U kunt nu Markdown-tabelcode rechtstreeks importeren met behulp van de tabelgegevens Bestand/Plakken... .



## 4. Kenmerken Analytics {#analytics-features}


| Nee | Functie | Beschrijving | Prioriteit |
|-----|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| 4.1 | Uitlijning van configuratiefunctie voor conversie | MVPD heeft metrisch voor verzoeken AuthN die met het SAML verzoek AuthN begint - om met de de verzoekmetriek van de Authentificatie van Primetime en van AuthN van de Programmer te richten. | A |
| 4.2 | Unieke gebruikers | Gebruikers die met succes zijn geverifieerd en waarvan het duplicaat maandelijks tijdens het bijwerken over dagen is verwijderd. | A |
| 4.3 | Tijdzoneboekhouding | Rapporten bevatten tijdzone voor wanneer de dag overgaat. | A |





## 5. Functies voor fraudebestrijding {#fraud-mitgn-features}


| Nee | Functie | Beschrijving | Prioriteit | Notities |
|-----|--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------|
| 5.1 | Validatie videoabonnee bij verificatie | MVPD zorgt ervoor dat de gebruiker een geldige videoabonnee tijdens de stroom AuthN is. | A |  |
| 5.2 | Snelheidlimiet voor verificatie/autorisatie | MVPD steunt het vertragen op hun Webdiensten om gebruik van een specifieke gebruikersrekening te beperken wanneer aangewezen. | B |  |
| 5.3 | Blijvende gebruikersnaam met algemeen bereik naar Adobe | MVPD zorgt ervoor dat Adobe een UserID heeft die over Programmers voor fraude kan worden gevolgd. Dit hoeft niet rechtstreeks aan de klant te worden geleverd. | B | Online Multimedia Authorization Protocol (OMAP) Specification and Real User Monitoring (RUM). |
| 5.4 | Validatie van gelijktijdig gebruik | MVPD heeft een middel om het gelijktijdige gebruik van de abonneerekening voorbij een bedrijfsdrempel te volgen en te beperken. | B |  |

## P1. Proxy-specifieke functies {#proxy-sp-func-features}

| Nee | Beschrijving | Prioriteit | Notities |
|-------|--------------------------------------------------------------------------------|----------|---------------------------------------------------|
| P 1.1 | Proxy verantwoordelijk voor het bijhouden van de nauwkeurigheid van de bijgewerkte lijst van subVPD&#39;s | A |  |
| P 1.2 | De volmacht levert aangewezen gerangschikte embleem voor elk subMVPD | A | Sommige levende subMVPDs hebben niet de juiste grootte van het embleem |
| P 1.3 | De volmacht levert geschikt branded login pagina voor elke subMVPD | A |  |
| P 1.4 | Proxy verantwoordelijk voor het richten van specifieke dienstverlener merken met subMVPD lijst | B |  |
| P 1.5 | Proxy geeft alle subMVPD-eigenschappen correct op (iFrame-grootte, TTL, logo, enz.) | A |  |
| P 1.6 | Proxy geeft een afzonderlijke entiteit-id op | B |  |

## P2. Operationele proxyfuncties {#proxy-op-features}

| Nee | Beschrijving | Prioriteit |
|-------|----------------------------------------------------------------------------------------|----------|
| P. 2.1 | API-sleutel is beveiligd | A |
| P 2.2 | De geloofsbrieven van de test voor eerste subMVPD die in levende integratie voor elke nieuwe aanvrager wordt gebruikt | A |
| P. 2.3 | SubVPD-lijsten zijn nauwkeurig en volledig per aanvrager | A |
