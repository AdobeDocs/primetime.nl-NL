---
title: Token voor korte media verkrijgen
description: short media token verkrijgen
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---


# Token voor korte media verkrijgen {#obtain-short-media-token}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## REST API-eindpunten {#clientless-endpoints}

&lt;reggie_fqdn>:

* Productie - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Productie - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>

## Beschrijving {#description}

Hiermee wordt een kort mediatoken opgehaald.  

| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/mediatoken</br></br>  of</br></br>&lt;sp_fqdn>/api/v1/tokens/media</br></br>Bijvoorbeeld:</br></br>&lt;sp_fqdn>/api/v1/tokens/media | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager (verplicht)</br>2.  deviceId (verplicht)</br>3.  bron (verplicht)</br>4.  device_info/X-Device-Info (verplicht)</br>5.  _deviceType_</br> 6.  _deviceUser_ (Afgekeurd)</br>7.  _appId_ (Afgekeurd) | GET | XML of JSON met een Base64-gecodeerde media-token of foutdetails als dit niet lukt. | 200 - Succes  </br>403 - Geen succes |

{style=&quot;table-layout:auto&quot;}

<!--
| Endpoint | Called  </br>By | Input   </br>Params | HTTP  </br>Method | Response | HTTP  </br>Response |
| --- | --- | --- | --- | --- | --- |
| `<SP_FQDN>/api/v1/mediatoken`</br></br>  or</br></br>`<SP_FQDN>/api/v1/tokens/media`</br></br>For example:</br></br>`<SP_FQDN>/api/v1/tokens/media` | Streaming App</br></br>or</br></br>Programmer Service | <ol><li>requestor (Mandatory)</l><li>deviceId (Mandatory)</li><li>resource (Mandatory)</li><li>device_info/X-Device-Info (Mandatory)</li><li>_deviceType_</li><li>_deviceUser_ (Deprecated)</li><li>_appId_ (Deprecated)</li></ol> | GET | XML or JSON containing an Base64 encoded media token or error details if unsuccessful. | 200 - Success  </br>403 - No Success |
-->

</br>

| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| deviceId | De id-bytes van het apparaat. |
| resource | Een koord dat een resourceId (of fragment MRSS) bevat, identificeert de inhoud die door een gebruiker wordt gevraagd en door MVPD vergunningseindpunten wordt erkend. |
| device_info/</br></br>X-Apparaat-Info | Informatie over streaming apparaat.</br></br>**Opmerking**: This MAY BE passed device_info as a URL parameter, but due to the potential size of this parameter and constraints on the length of a GET URL, it should be passed as X-Device-Info in the http header. </br></br>Zie de volledige details in [Gegevens van apparaat en verbinding doorgeven](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Het apparaattype (bijvoorbeeld Roku, PC).</br></br>Als deze parameter correct is ingesteld, biedt ESM metriek die [uitgesplitst per apparaattype](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) bij gebruik van Clientless, zodat verschillende soorten analyses kunnen worden uitgevoerd voor bijvoorbeeld Roku, AppleTV, Xbox enz.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**Opmerking**: device_info zal deze parameter vervangen. |
| _deviceUser_ | De gebruikers-id van het apparaat.</br></br>**Opmerking**: Indien gebruikt, moet deviceUser dezelfde waarden hebben als in het dialoogvenster [Registratiecode maken](http://tve.helpdocsonline.com/registration-code-request) verzoek. |
| _appId_ | De toepassings-id/-naam. </br></br>**Opmerking**: device_info vervangt deze parameter. Indien gebruikt, `appId` moeten dezelfde waarden hebben als in de [Registratiecode maken](http://tve.helpdocsonline.com/create-registration-page-/-login-uri) verzoek. |

{style=&quot;table-layout:auto&quot;}

### Samplereactie {#response}

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <play>
        <expires>1348649569000</expires>
        <mvpdId>sampleMvpdId</mvpdId>
        <requestor>sampleRequestorId</requestor>
        <resource>sampleResourceId</resource>
        <serializedToken>PHNpZ25hdH[...]</serializedToken>
        <userId>sampleScrambledUserId</userId>
    </play>
```



**JSON:**

```JSON
    {
        "resource": "sampleResourceId",
        "requestor": "sampleRequestorId",
        "expires": "1348649614000",
        "serializedToken": "PHNpZ25hdH[...]",
        "userId": "sampleScrambledUserId",
        "mvpdId": "sampleMvpdId"
    }
```

 

### Compatibiliteit van de mediaverificatiebibliotheek

Het veld `serializedToken` van de vraag &quot;verkrijgen Korte Token van Media&quot;is een Base64 gecodeerde teken dat tegen de Bibliotheek van de Verificatie van Adobe Media kan worden geverifieerd.

[Terug naar REST API-naslaggids](http://tve.helpdocsonline.com/rest-api-reference)
