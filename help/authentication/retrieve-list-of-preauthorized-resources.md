---
title: Lijst met vooraf gemachtigde bronnen ophalen
description: Lijst met vooraf gemachtigde bronnen ophalen
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# Lijst met vooraf gemachtigde bronnen ophalen {#retrieve-list-of-preauthorized-resources}

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

Een verzoek aan de authentificatie van Adobe Primetime om de lijst van vooraf erkende middelen te verkrijgen.

Er zijn twee sets API&#39;s: één set voor de Streaming App of Programmer Service en één set voor de Second Screen Web App. Op deze pagina wordt de API voor de Streaming App of Programmer Service beschreven.


| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/preAuthze | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager (verplicht)</br>2.  deviceId (verplicht)</br>3.  resourcerelijst (verplicht)</br>4.  device_info/X-Device-Info (verplicht)</br>5.  _deviceType_</br> 6.  _deviceUser_ (Afgekeurd)</br>7.  _appId_ (Afgekeurd) | GET | XML of JSON met individuele aan de autorisatie voorafgaande beslissingen of foutdetails. Zie onderstaande voorbeelden. | 200 - Succes</br></br>400 - Onjuist verzoek</br></br>401 - Niet-geautoriseerd</br></br>405 - Methode niet toegestaan  </br></br>412 - Voorwaarde is mislukt</br></br>500 - Interne serverfout |


| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| deviceId | De id-bytes van het apparaat. |
| resourcerelijst | Een tekenreeks die een door komma&#39;s gescheiden lijst met resourceIds bevat die de inhoud identificeert die toegankelijk kan zijn voor een gebruiker en die wordt herkend door MVPD-autorisatieeindpunten. |
| device_info/</br></br>X-Apparaat-Info | Informatie over streaming apparaat.</br></br>**Opmerking**: This MAY BE passed device_info as a URL parameter, but due to the potential size of this parameter and constraints on the length of a GET URL, it should be passed as X-Device-Info in the http header. </br></br>Zie de volledige details in [Gegevens van apparaat en verbinding doorgeven](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Het apparaattype (bijvoorbeeld Roku, PC).</br></br>Als deze parameter correct is ingesteld, biedt ESM metriek die [uitgesplitst per apparaattype](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) bij gebruik van Clientless, zodat verschillende soorten analyses kunnen worden uitgevoerd voor bijvoorbeeld Roku, AppleTV, Xbox enz.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**Opmerking**: device_info zal deze parameter vervangen. |
| _deviceUser_ | De gebruikers-id van het apparaat. |
| _appId_ | De toepassings-id/-naam. </br></br>**Opmerking**: device_info vervangt deze parameter. |



### Samplereactie {#sample-response}

 

**XML:**

```XML
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4
Adobe-Response-Confidence : full
Content-Type: application/xml; charset=utf-8

<resources>
  <resource>
    <id>TestStream1</id>
    <authorized>true</authorized>
  </resource>
  <resource>
    <id>TestStream2</id>
    <authorized>false</authorized>
    <error>
      <status>403</status>
      <code>authorization_denied_by_mvpd</code>
      <message>User not authorized</message>
      <details>Your subscription package does not include the "TestStream3" channel.</details>
      <helpUrl>https://tve.helpdocsonline.com/errors/preauthorization_denied</helpUrl>
      <trace>0453f8c8-167a-4429-8784-cd32cfeaee58</trace>
      <action>none</action>
    </error>
  </resource>
</resources>
```
 
</br>

**JSON:**

```JSON
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4
Adobe-Response-Confidence : full
Content-Type: application/json; charset=utf-8
 
{
   "resources" : [
        {
            "id" : "TestStream1",
            "authorized" : true
        },
        {
            "id" : "TestStream3",
            "authorized" : false,
            "error" : {
               "status" : 403,
               "code" : "authorization_denied_by_mvpd",
               "message" : "User not authorized",
               "details" : "Your subscription package does not include the "TestStream3" channel.",
               "helpUrl" : "https://tve.helpdocsonline.com/errors/preauthorization_denied",
               "trace" : "0453f8c8-167a-4429-8784-cd32cfeaee58",
               "action" : "none"
            }
        } 
    ]
}
```


### [Terug naar REST API-naslaggids](http://tve.helpdocsonline.com/rest-api-reference)
