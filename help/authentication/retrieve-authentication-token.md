---
title: Verificatietoken ophalen
description: Verificatietoken ophalen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Verificatietoken ophalen {#retrieve-authentication-token}

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

Hiermee wordt het verificatietoken (AuthN) opgehaald.  

| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/authoring</br></br>Bijvoorbeeld:</br></br>&lt;sp_fqdn>/api/v1/tokens/authoring | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager (verplicht)</br>2.  deviceId (verplicht)</br>3.  device_info/X-Device-Info (verplicht)</br>4.  _deviceType_ (Afgekeurd)</br>5.  _deviceUser_ (Afgekeurd)</br>6.  _appId_ (Afgekeurd) | GET | XML of JSON met verificatiegegevens of foutdetails als dit mislukt. | 200 - Geslaagd.  </br>404 - token niet gevonden  </br>410 - token verlopen |

{style=&quot;table-layout:auto&quot;}


| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| deviceId | De id-bytes van het apparaat. |
| device_info/</br></br>X-Apparaat-Info | Informatie over streaming apparaat.</br></br>**Opmerking**: This MAY BE passed device_info as a URL parameter, but due to the potential size of this parameter and constraints on the length of a GET URL, it should be passed as X-Device-Info in the http header. </br></br>Zie de volledige details in [Gegevens van apparaat en verbinding doorgeven](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Het apparaattype (bijvoorbeeld Roku, PC).</br></br>**Opmerking**: device_info vervangt deze parameter. |
| _deviceUser_ | De gebruikers-id van het apparaat.</br></br>**Opmerking**: Indien gebruikt, moet deviceUser dezelfde waarden hebben als in het dialoogvenster [Registratiecode maken](http://tve.helpdocsonline.com/registration-code-request) verzoek. |
| _appId_ | De toepassings-id/-naam. </br></br>**Opmerking**: device_info vervangt deze parameter. Indien gebruikt, `appId` moeten dezelfde waarden hebben als in de [Registratiecode maken](http://tve.helpdocsonline.com/registration-code-request) verzoek. |

{style=&quot;table-layout:auto&quot;}

</br>

### Samplereactie {#response}

 

#### Succes

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <authentication>
         <expires>1601114932000</expires>
         <userId>sampleUserId</userId>
         <mvpd>sampleMvpdId</mvpd>
         <requestor>sampleRequestor</requestor>
    </authentication>
```


**JSON:**

```JSON
    {
         "requestor": "sampleRequestor",
         "mvpd": "sampleMvpdId",
         "userId": "sampleUserId",
         "expires": "1601114932000"
    }
```

 

 

#### Verificatietoken niet gevonden:

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <error>
        <status>404</status>
        <message>Not found</message>
    </error>
```

 
**JSON:**

```JSON
    {
        "status": 404,
        "message": "Not Found"
    }
```

[Terug naar API-naslaggids voor clients](http://tve.helpdocsonline.com/clientless-api-reference)
