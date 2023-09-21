---
title: Rapport-API
description: API voor Auditude-rapport
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 1%

---

# Rapport-API {#report-api}

De gebruikersinterface heeft beheerde rollen voor klanten en voor het (Adobe) team van Enablement. Klanten hebben toegang tot het portaal en kunnen vervolgens hun configuraties maken en bewerken. Ze kunnen ook de rapporten voor hun advertentie-impressies in de gebruikersinterface zien.

API&#39;s werken achter de schermen om klanten en beheerders te helpen te communiceren met de back-endinfrastructuur.

Om de [!DNL Primetime Ad Insertion] APIs zie [Ad Insertion API-eindpunten in gevloeide gebruikersinterface](https://adconfigservice-va6.cloud.adobe.io/swagger-ui/index.html#/).

## API-eindpunt {#report-api-endpoint}

### Productie {#production}

`https://dai-primetime.adobe.io/report`

### Sandbox {#sandbox}

`https://dai-sandbox1-primetime.adobe.io/report`

## Zoekparameters


| Naam | Significantie | Type waarde | Verplicht? | Standaardwaarde | Restricties | Voorbeeld/Geldige samplewaarden |
|----------|-----------------------------------------------------------------------------------------------|----------------|----------------|---------------------|------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| endDate | Einddatum voor de rapportgegevens | date | Y | GEEN | niet nieuwer dan gisteren in UTC-8 | ######## |
| filters | filteren op een of meer kolommen | string | N | GEEN | ad_config_id , zone_id | ad_config_id=990,900;state=active |
|          |                                                                                               |                |                |                     | Wanneer metaData in de aanvraag op &#39;true&#39; is ingesteld, kunt u ook filteren op naam. |                                                                         |
|          |                                                                                               |                |                |                     |                                                                                    | Meerdere filtersleutels zijn door een puntkomma gescheiden. |
|          |                                                                                               |                |                |                     |                                                                                    | Gebruik door komma&#39;s gescheiden waarden om een lijst met waarden voor filtersleutel op te geven |
| groupBy | Groepeer op tijd ( jaar \| maand \| dag) of ad_config_id. Adconfig is synoniem van AdRule. | string | N | GEEN | y \| m \| d , ad_config_id | m, ad_config_id |
|          |                                                                                               |                |                |                     |                                                                                    |                                                                         |
|          |                                                                                               |                |                |                     |                                                                                    | Geef voor groupBy op tijd een van y of m of d op |
|          |                                                                                               |                |                |                     |                                                                                    |                                                                         |



## Kopteksten {#headers}

| Naam | Type waarde | Verplicht | Samplewaarde | Significantie |
|-----------------------|----------------|---------------|-------------------------------------|------------------------------------|
| Accepteren | string | Y | text/csv voor CSV | Type reactie verwacht van API |
|                       |                |               | application/json of &#39;*/*&#39; voor JSON |                                    |
| Token voor autorisatie | string | Y | xyz | machtigingstoken |
| x-api-key | string | Y | xyz | API-sleutel |
| x-gw-ims-org-id | string | Y | xyz12345 | IMS org-id van uw account |

* U kunt het token voor autorisatie (ook wel toegangstoken genoemd) genereren door de stappen te volgen die worden beschreven in de JWT-verificatieHelp-pagina van Adobe.io.
  >>
  [!NOTE]
  >Het teken van de vergunning heeft een vervaldatum van 24 uren, zodat als u Rapport API gebruikend een terugkerend manuscript gebruikt, dan zorg ervoor u auteur vóór zijn vervaldatum produceert of wanneer u een fout Oauth over het teken krijgt niet geldig is.

* Als u de juiste waarden in de aanvraagheader wilt instellen en een machtigingstoken wilt genereren (met JWT-verificatie), moet u de onderstaande configuraties voor uw account kennen. Neem contact op met het Primetime-ondersteuningsteam voor deze waarden.
Id van technische rekening

   * Org-id
   * Api_key
   * Client_sensitive

## Uitvoer {#output}

Het resultaat van de API-query van het rapport is standaard in de JSON-indeling, die de afbeeldingen instelt tegen de verschillende waarden van de aangevraagde afmetingen (groupby param). De voorbeelduitvoer wordt hieronder gegeven:

```JSON
[
    {
        "dates": "07-2020",
        "total_impressions": 213007041
    },
    {
        "dates": "08-2020",
        "total_impressions": 174711626
    },
    {
        "dates": "09-2020",
        "total_impressions": 102863153
    }
]
```

## Foutcodes en -tekenreeksen {#error-codes-strings}

### Error Response Format {#error-response-format}

Fout bij het renderen van macro&#39;code: ongeldige waarde opgegeven voor parameter `com.atlassian.confluence.ext.code.render.InvalidValueException`

```Shell
{
"error_code": "<ERROR_CODE>",
"message": "<ERROR_MESSAGE>"
}
```

In de onderstaande tabel staan de foutcodes en berichten die de rapportAPI kan retourneren. Raadpleeg voor fouten met betrekking tot de machtigingslaag de [foutcodedocumentatie](https://experienceleague.adobe.com/docs/experience-platform/landing/troubleshooting.html?lang=en#errors-and-troubleshooting) van Adobe.io.

| Foutcode | Foutbericht |
|-----------------------|------------------------------------------|
| 4001007 | Gebruikersdetails zijn ongeldig. |
| 4001008 | Alle zones zijn niet van hetzelfde account. |
| 5001010 | Er is een interne fout opgetreden. |
| 4001011 | Datums worden niet in de vereiste indeling verzonden. |
| 4001012 | Datums liggen buiten het bereik. |
| 4001013 | De verplichte parameter ontbreekt. |
| 4001014 | De lijst met zones is leeg voor de account. |
| 4001015 | Ongeldige filtertoetsen in aanvraag. |
| 4001016 | Ongeldige optie GroupBy in aanvraag. |
| 4001017 | Ongeldige id is opgegeven in aanvraag |

## De Vraag van de steekproef en verwachte resultaten {#sample-calls-expected-results}

Hier volgt de curl-opdracht voor het maandelijks tellen van de indruk tussen 2020-07-01 en 2021-06-30 met behulp van toegangstoken:

**Voorbeeld van API-aanroep melden**

```shell
curl --location --request GET 'https://dai-sandbox1-primetime.adobe.io/report?startDate=2020-07-01&endDate=2021-06-30&groupBy=m&unpaged=true' \
--header 'x-api-key: <API_KEY>' \
--header 'x-gw-ims-org-id: <ORG_ID>' \
--header 'Authorization: Bearer <ACCESS_TOKEN_STRING>' \
--header 'Accept: application/json'
```

| Voorbeeld: Bellen/Hoofdletters gebruiken | Verwacht resultaat |
|---|---|
| Ophaalrapport met begin- en einddatum GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2021-01-01 header : Accept = application/json. of */* | Json met de volgende parameters met alle advertenties die tot deze account behoren total_impressions |
| Rapport ophalen met GroupBy = d \| m \| y GET: [API_ENDPOINT]//rapport?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d \| m \| y header : Accept = application/json. of */* | Json met de volgende parameters met alle advertenties die tot deze accountdatums behoren (mm-dd-jjjj \| mm-jjjj \| jjjj formaat) total_impressions |
| Rapport ophalen met GroupBy = ad_config_id GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=ad_config_id header : Accept = application/json. of */* | Json met de volgende parameters met alle advertenties die tot dit account behoren ad_config_id total_impressions |
| Rapport ophalen met GroupBy = d \| m \| y en ad_config_id GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d,ad_config_id header : Accept = application/json. of */* | Json met de volgende parameters met alle advertenties die tot deze account behoren: data ad_config_id (mm-dd-jjjj \| mm-jjjj \| jjjj formaat) total_impressions |
| Rapport ophalen met metaData=true en groupBy=d \| m \| y GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=ad_config_id header : Accept = application/json. of */* | Json met de volgende parameters met alle advertenties die tot deze account behoren: add_config_id name total_impressions |
| Rapport ophalen met groupBy=d \| m \| y en ad_config_id GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=d \| m \| y,ad_config_id header : Accept = application/json. of */* | Json met de volgende parameters met alle advertenties die tot deze account behoren: ad_config_id name total_impressions dates (mm-dd-jjjj \| mm-jjjj \| jjjj formaat) |
| Rapport ophalen om alle rijen voor een bepaald datumbereik op te halen (met unpaged = true) GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;groupBy=d&amp;unpaged=true | 31 items in de geretourneerde Json-array |
| Rapport ophalen met geldige GET voor paginaquery&#39;s: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;page=0&amp;size=5&amp;groupBy=d | 5 items in de geretourneerde array |
| Ophaalrapport, met csv-indeling GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10 header : Accept = text/csv | CSV string is returned, with header: total_impressions |
| Zoekrapport, met CSV-indeling, en groupBy = d \| m \| y GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;groupBy=d\|m\|y header : Accept = text/csv | CSV string is returned, with header: total_impressions dates (mm-dd-yyyy \| mm-yyyy \| yyyy format) |
| Rapport ophalen, met CSV-indeling, en metagegevens = true GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true header : Accept = text/csv | CSV string is returned, with header: total_impressions |
| Rapport ophalen, met csv-indeling, metadata = true en groupBy = d \| m \| y GET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true&amp;groupBy=d\|m\|y header : Accept = text/csv | CSV string is returned, with header: total_impressions dates (mm-dd-yyyy \| mm-yyyy \| yyyy format) |


## Beleid voor het doorsturen van API&#39;s rapporteren {#report-api-throttling-policy}

* 5 API-aanvragen zijn toegestaan tijdens een venster van 5 seconden voor elke gebruiker.
* Wanneer een gebruiker de bovenstaande limiet overschrijdt, wordt de respons 5 seconden vertraagd.
* Als een gebruiker meer dan 10 vraag binnen 5 tweede venster maakt, zullen zij worden verworpen met antwoord &quot;429 Te veel verzoeken&quot;.
