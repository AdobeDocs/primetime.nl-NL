---
title: Vooraf autoriseren
description: JavaScript vooraf autoriseren
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 0%

---


# Vooraf autoriseren {#js-preauthorize}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Overzicht {#preauth-overview}

De methode van de preauthorize API moet door toepassingen worden gebruikt om pre-vergunningsbesluiten voor één of meerdere middelen te verkrijgen. De aanvraag van de API voor voorafgaande toestemming moet worden gebruikt voor UI-tips en/of het filteren van inhoud. Een daadwerkelijke vergunning API verzoek moet worden gemaakt alvorens gebruikerstoegang tot de gespecificeerde middelen toe te staan.

Als er een onverwachte fout optreedt (bijvoorbeeld netwerkprobleem en MVPD-autorisatiepunt niet beschikbaar) wanneer een aanvraag voor een voorafgaande API wordt verwerkt door de Adobe Primetime-verificatieservices, wordt er een of meer afzonderlijke foutinformatie opgenomen voor de betrokken bronnen als onderdeel van het resultaat van de eerdere API-reactie.

### public preauthorize(request: PreAuthzeRequest, callback: AccessEnablerCallback&lt;any>): void {#preauth-method}

**Omschrijving:** Deze methode moet door toepassingen worden gebruikt om de (informatieve) beslissingen van geverifieerde gebruikers vooraf te verkrijgen van de Adobe Primetime-verificatieservice om specifieke beveiligde bronnen weer te geven, met als voornaamste doel de gebruikersinterface van de toepassing te versieren (bijvoorbeeld om de toegangsstatus met vergrendelings- en ontgrendelingspictogrammen aan te geven).

**Beschikbaarheid:** v4.4.0+

**Parameters:**

* `PreauthorizeRequest`: Builder-object dat wordt gebruikt om het verzoek te definiëren
* `AccessEnablerCallback`: callback die wordt gebruikt om de API reactie terug te keren
* `PreauthorizeResponse`: Object dat wordt gebruikt om de inhoud van de API-reactie te retourneren

### class PreAuthzeRequestBuilder {#preath-req-builder-class}

#### setResources(resources: string[]): PreauthorizeRequestBuilder {#set-res-preath-req-buildr}

* Hiermee stelt u de lijst met bronnen in waarvoor u voorafgaande autorisatiebeslissingen wilt verkrijgen.
* Het is verplicht deze in te stellen voor het gebruik van de voorafgaande autorisatie-API.
* Elk element in de lijst moet een Koord zijn die of de waarde van middelidentiteitskaart of het mediaRSS fragment vertegenwoordigen dat met MVPD moet worden overeengekomen.
* Deze methode stelt de informatie alleen in in de context van de huidige `PreauthorizeRequestBuilder` objectinstantie, die de ontvanger is van deze methodeaanroep.

* Een daadwerkelijke `PreauthorizeRequest` u kunt een blik hebben `PreauthorizeRequestBuilder`s methode:

```JavaScript
  build(): PreauthorizeRequest
```

* `@param {string[]}` middelen. De lijst van middelen waarvoor u pre-vergunningsbesluiten wilt verkrijgen.
* `@returns {PreauthorizeRequestBuilder}` De verwijzing naar hetzelfde `PreauthorizeRequestBuilder` objectinstantie, die de ontvanger is van de methodeaanroep.
* Het doet dit om het creëren van methode het ketenen toe te staan.

#### disableFeatures(...functies: string[]): PreauthorizeRequestBuilder {#disabl-featres-preauth-req-buildr}

* Hiermee stelt u de functies in die u wilt uitschakelen bij het verkrijgen van beslissingen vóór toelating.
* Deze functie stelt de informatie alleen in in de context van de huidige `PreauthorizeRequestBuilder` objectinstantie, die de ontvanger is van deze functieaanroep.
* Een daadwerkelijke `PreauthorizeRequest` u kunt een blik hebben `PreauthorizeRequestBuilder`s functie:

```JavaScript
public func build() -> PreauthorizeRequest
```

* `@param {string[]}` functies. De reeks functies die u wilt uitschakelen.
* `@returns` De verwijzing naar hetzelfde `PreauthorizeRequestBuilder` objectinstantie, die de ontvanger is van de functieaanroep.
* Het doet dit om het creëren van functie ketting toe te staan.

#### build(): PreauthorizeRequest {#preauth-req}

* Hiermee maakt en haalt u de referentie van een nieuwe `PreauthorizeRequest` objectinstantie.
* Deze methode instantieert een nieuw `PreauthorizeRequest` object telkens wanneer het wordt aangeroepen.
* Deze methode gebruikt de vooraf ingestelde waarden in de context van de huidige `PreauthorizeRequestBuilder` objectinstantie, die de ontvanger is van deze methodeaanroep.
* Houd er rekening mee dat deze methode geen bijwerkingen veroorzaakt.
* De staat van de SDK of de staat van de SDK wordt derhalve niet gewijzigd `PreauthorizeRequestBuilder` objectinstantie, die de ontvanger is van deze methodeaanroep.
* Het betekent dat de opeenvolgende vraag van deze methode voor de zelfde ontvanger tot verschillende nieuwe zal leiden `PreauthorizeRequest` objectinstanties, maar met dezelfde informatie, voor het geval de waarden op de `PreauthorizeRequestBuilder` waar niet gewijzigd tussen de vraag.
* Als u geen van de verschafte informatie (bronnen en caching) hoeft bij te werken, kunt u de instantie PreauthorizeRequest opnieuw gebruiken voor meerdere toepassingen van de API voor voorafgaande toestemming.
* `@returns {PreauthorizeRequest}`

### interface AccessEnablerCallback&lt;t> {#interface-access-enablr-callback}

#### onResponse(result): T) {#on-response-result}

* De callback van de reactie die door SDK wordt geroepen toen de preauthorize API verzoek werd vervuld.
* Het resultaat is een geslaagd resultaat of een foutresultaat met een status.
* `@param {T} result`

#### onFailed(result: T) {#on-failure-result}

* De mislukte callback die door SDK wordt geroepen wanneer het preauthorize API verzoek kon niet worden onderhouden.
* Het resultaat is een mislukkingsresultaat dat een status bevat.
* `@param {T} result`

### klasse PreauthorizeResponse {#preauth-response-class}

#### status van het publiek: Status; {#public-status}

* Retourneert: Aanvullende status (status)-informatie in geval van een storing.
* Houd mogelijk een `null` waarde.

#### openbare besluiten : Besluit[]; {#public-decisions}

* Retourneert: De lijst van besluiten tot voorafgaande toestemming. Eén besluit voor elke bron.
* De lijst kan leeg zijn in het geval van een fout.

### klassestatus {#class-status}

#### status van het publiek: nummer; {#public-status-numbr}

* De HTTP-antwoordstatuscode zoals beschreven in RFC 7231.
* Kan 0 zijn voor het geval dat de `Status` is afkomstig van de SDK in plaats van de Adobe Primetime-verificatieservices.

#### openbare code: nummer; {#public-code-numbr}

* De standaardfoutcode voor Adobe Primetime-verificatieservices.
* Kan een lege tekenreeks of een `null` waarde.

#### openbaar bericht: tekenreeks; {#public-msg-string}

* Het gedetailleerde bericht dat in sommige gevallen wordt verstrekt door de MVPD toestemmingseindpunten of door de degradatieregels van de Programmer.
* Kan een lege tekenreeks of een `null` waarde.

#### openbare gegevens: tekenreeks; {#public-details-strng}

* Bevat een gedetailleerd bericht dat in sommige gevallen wordt verstrekt door de MVPD toestemmingseindpunten of door de degradatieregels van de Programmer.
* Kan een lege tekenreeks of een `null` waarde.


#### public helpUrl: tekenreeks; {#public-help-url-string}

* De URL die een koppeling vormt naar meer informatie over de oorzaak van deze fout en mogelijke oplossingen.
* Kan een lege tekenreeks of een `null` waarde.

#### public trace: tekenreeks; {#public-trace-string}

* De unieke id voor deze reactie, die kan worden gebruikt wanneer contact wordt opgenomen met ondersteuning om specifieke problemen in complexere scenario&#39;s te identificeren.
* Kan een lege tekenreeks of een `null` waarde.

#### openbare actie: tekenreeks; {#public-action-string}

* De aanbevolen maatregelen om de situatie te verhelpen.
   * **none**: Helaas is er geen vooraf gedefinieerde actie om dit probleem op te lossen. Dit kan wijzen op een onjuiste aanroep van de openbare API
   * **configuratie**: Een configuratiewijziging is nodig via het TVE-dashboard of door contact op te nemen met de technische ondersteuning.
   * **inschrijving**: De toepassing moet zich opnieuw registreren.
   * **verificatie**: De gebruiker moet verifiëren of opnieuw verifiëren.
   * **autorisatie**: De gebruiker moet toestemming voor de specifieke bron verkrijgen.
   * **aantasting**: Er moet enige vorm van afbraak worden toegepast.
   * **opnieuw proberen**: Het opnieuw proberen van het verzoek zou de kwestie kunnen oplossen
   * **retry-after**: Het opnieuw proberen van het verzoek na de aangegeven periode zou de kwestie kunnen oplossen.
* Kan een lege tekenreeks of een `null` waarde.

### klasse-besluit {#class-decision}

#### public id: tekenreeks; {#public-id-string}

* De bron-id waarvoor het besluit is genomen.

#### met toestemming van het publiek: Booleaans; {#public-auth-boolean}

* De waarde van de markering die aangeeft of de beslissing succesvol is of niet.

#### openbare fout: Status; {#public-error-status}

* Aanvullende status (status)-informatie voor het geval er een fout optreedt. Houd mogelijk een `null` waarde.

## Voorbeeld van implementatie van client {#client-imp-example}

```JavaScript
let accessEnablerApi = new window.AccessEnabler.AccessEnabler("software statement");
let accessEnablerModels = window.AccessEnabler.models;



// Build request
let requestBuilder = new accessEnablerModels.PreauthorizeRequest.getBuilder();
let request = requestBuilder
    .setResources(["RES01", "RES02", "RES03"])
    .disableFeatures("LOCAL_CACHE")
    .build();



// Create callback
let callback = {
    onResponse(response) {
        // Handle onResponse
    },
    onFailure(response) {
        // Handle onFailure
    }
};

// Invoke call
accessEnablerApi.preauthorize(request, callback);
```


## Scenario-voorbeelden {#scenario-examples}

### Scenario 1: Alle gevraagde middelen zijn geautoriseerd {#all-req-res-auth}

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Uitgeschakeld</td>
    <td>

```JavaScript
        {
    "decisions": [
        {
        "id": "RES01",
        "authorized": true
        },
        {
        "id": "RES02",
        "authorized": true
        },
        {
        "id": "RES03",
        "authorized": true
        }
    ]
    }    
```

</td>
  </tr>
</tbody>


### Scenario 2: Sommige gevraagde middelen zijn toegestaan. {#sm-req-res-auth}

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Uitgeschakeld</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;besluiten&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;toegelaten&quot;: true
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;toegelaten&quot;: false
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;toegelaten&quot;: true
    }
    ]
    }
    
    &quot;

</td>
  </tr>

<tr>
    <td>Ingeschakeld</td>
    <td>

    &quot;JavaScript
    {
    &quot;besluiten&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;toegelaten&quot;: true
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;toegelaten&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403
    &quot;code&quot;: &quot;preauthentication_deny_by_mvpd&quot;,
    &quot;bericht&quot;: &quot;MVPD heeft een &quot;Weigeren\&quot;besluit teruggegeven toen het verzoeken van pre-vergunning voor het gespecificeerde middel.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;toegelaten&quot;: true
    },
    ]
    }
    
    &quot;

</td>
  </tr>
</tbody>


### Scenario 3: Geen van de gevraagde middelen werd toegestaan. {#none-req-res-auth}

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Uitgeschakeld</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;besluiten&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;toegelaten&quot;: false
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;toegelaten&quot;: false
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;toegelaten&quot;: false
    }
    ]
    }
    
    &quot;

</td>
  </tr>

<tr>
    <td>Ingeschakeld</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;besluiten&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;toegelaten&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403
    &quot;code&quot;: &quot;preauthentication_deny_by_mvpd&quot;,
    &quot;bericht&quot;: &quot;MVPD heeft een &quot;Weigeren\&quot;besluit teruggegeven toen het verzoeken van pre-vergunning voor het gespecificeerde middel.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;toegelaten&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403
    &quot;code&quot;: &quot;preauthentication_deny_by_mvpd&quot;,
    &quot;bericht&quot;: &quot;MVPD heeft een &quot;Weigeren\&quot;besluit teruggegeven toen het verzoeken van pre-vergunning voor het gespecificeerde middel.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;toegelaten&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403
    &quot;code&quot;: &quot;maximum_execute_time_over&quot;,
    &quot;bericht&quot;: &quot;Het verzoek is niet binnen de maximaal toegestane tijd voltooid. Het opnieuw proberen van het verzoek zou de kwestie kunnen oplossen.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;retry&quot;
    }
    }
    ]
    }
    
    &quot;

</td>
  </tr>
</tbody>


### Scenario 4: Onjuist clientverzoek - geen bronnen opgegeven. {#bad-cl-req-no-res-sp}

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Uitgeschakeld/Ingeschakeld</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 400
    &quot;code&quot;: &quot;internal_error&quot;,
    &quot;bericht&quot;: &quot;De aanvraag is mislukt als gevolg van een interne fout.&quot;,
    &quot;details&quot;: &quot;Required String[] parameter &#39;resource&#39; is not present&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;none&quot;
    },
    &quot;besluiten&quot;: []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Scenario 5: Onjuist clientverzoek - er zijn lege bronnen opgegeven. {#bad-cl-req-empt-res-sp}

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Uitgeschakeld/Ingeschakeld</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 412
    &quot;code&quot;: &quot;missing_resource&quot;,
    &quot;bericht&quot;: &quot;De parameter resource ontbreekt&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;none&quot;
    },
    &quot;besluiten&quot;: []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Scenario 6: Netwerkfout. {#ntwrk-error}

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Ingeschakeld</td>
    <td>

    &quot;JavaScript
    {
    &quot;besluiten&quot;: [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;toegelaten&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403
    &quot;code&quot;: &quot;network_receive_error&quot;,
    &quot;bericht&quot;: &quot;Er was een gelezen fout terwijl het terugwinnen van de reactie van de bijbehorende partnerdienst. Het opnieuw proberen van het verzoek zou de kwestie kunnen oplossen.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;retry&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;toegelaten&quot;: false,
    &quot;error&quot;: {
    &quot;status&quot;: 403
    &quot;code&quot;: &quot;network_receive_error&quot;,
    &quot;bericht&quot;: &quot;Er was een gelezen fout terwijl het terugwinnen van de reactie van de bijbehorende partnerdienst. Het opnieuw proberen van het verzoek zou de kwestie kunnen oplossen.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;actie&quot;: &quot;retry&quot;
    }
    }
    ]
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Scenario 7: De flow voor vooraf autoriseren is aangeroepen zonder een geldige AuthN-sessie.

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Uitgeschakeld/Ingeschakeld</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 0
    &quot;code&quot;: &quot;authentication_session_missing&quot;,
    &quot;bericht&quot;: &quot;De verificatiesessie die aan deze aanvraag is gekoppeld, kan niet worden opgehaald. De gebruiker moet met gesteund MVPD opnieuw voor authentiek verklaren om verder te gaan.&quot;,
    &quot;actie&quot;: &quot;authenticatie&quot;
    },
    &quot;besluiten&quot;: []
    }
    
    &quot;

</td>
  </tr>
</tbody>
</table>



### Scenario 8: De flow vooraf autoriseren werd aangeroepen voordat de aanroep setRequestor werd voltooid

<table>
<thead>
  <tr>
    <th>Markering voor verbeterde foutcode</th>
    <th>Antwoord</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Uitgeschakeld/Ingeschakeld</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 0
    &quot;code&quot;: &quot;requestor_not_configured&quot;,
    &quot;bericht&quot;: &quot;De aanvrager is nog niet geconfigureerd wat een vereiste is voor het gebruik van een API, behalve de setRequestor-API.&quot;,
    &quot;actie&quot;: &quot;retry&quot;
    },
    &quot;besluiten&quot;: []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

