---
title: Verificatietoken controleren
description: Verificatietoken controleren
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Verificatietoken controleren {#check-authentication-token}

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

Geeft aan of het apparaat een niet-verlopen verificatietoken heeft.

| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/checkauthing | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager (verplicht)</br>2.  deviceId (verplicht)</br>3.  device_info/X-Device-Info (verplicht)</br>4.  _deviceType_ </br>5.  _deviceUser_ (Afgekeurd)</br>6.  _appId_ (Afgekeurd) | GET | XML of JSON met foutdetails als dit mislukt. | 200 - Succes   </br>403 - Geen succes |

{style=&quot;table-layout:auto&quot;}


| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| deviceId | De id-bytes van het apparaat. |
| device_info/</br></br>X-Apparaat-Info | Informatie over streaming apparaat.</br></br>**Opmerking**: DIT KAN device_info als parameter URL worden overgegaan, maar wegens de potentiële grootte van deze parameter en beperkingen op de lengte van een GET URL, ZOU het als x-Apparaat-Info in de HTTP- kopbal moeten worden overgegaan. </br></br>Zie de volledige details in [Gegevens van apparaat en verbinding doorgeven](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Het apparaattype (bijvoorbeeld Roku, PC).</br></br>Als deze parameter correct is ingesteld, biedt ESM metriek die [uitgesplitst per apparaattype](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) bij gebruik van Clientless, zodat verschillende soorten analyses kunnen worden uitgevoerd voor bijvoorbeeld Roku, AppleTV, Xbox enz.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br>**Opmerking**: device_info zal deze parameter vervangen. |
| _deviceUser_ | De gebruikers-id van het apparaat. |
| _appId_ | De toepassings-id/-naam.</br>**Opmerking**: device_info vervangt deze parameter. |

{style=&quot;table-layout:auto&quot;}


## Reactie (indien mislukt) {#response}

```JSON
    <error>
      <status>403</status>
      <message>Authentication token expired</message>
    </error>
```

### [Terug naar REST API-naslaggids](http://tve.helpdocsonline.com/rest-api-reference)
