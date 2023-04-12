---
title: Afmelden starten
description: Afmelden starten
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Afmelden starten {#initiate-logout}

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

AuthN en AuthZ tekenen uit opslag verwijderen.


| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/logout | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager</br>2.  deviceId (verplicht)</br>3.  device_info/X-Device-Info (verplicht)</br>4.  _deviceType_</br> 5.  _deviceUser_ (Afgekeurd)</br>6.  _appId_ (Afgekeurd) | DELETE | Geen | 204 |


| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| deviceId | De id-bytes van het apparaat. |
| device_info/</br></br>X-Apparaat-Info | Informatie over streaming apparaat.</br></br>**Opmerking**: This MAY BE passed device_info as a URL parameter, but due to the potential size of this parameter and constraints on the length of a GET URL, it should be passed as X-Device-Info in the http header. </br></br><!--See the full details in [Passing Device and Connection Information](http://tve.helpdocsonline.com/passing-device-information)-->. |
| _deviceType_ | Het apparaattype (bijvoorbeeld Roku, PC).</br></br>Als deze parameter correct is ingesteld, biedt ESM metriek die [uitgesplitst per apparaattype](/help/authentication/entitlement-service-monitoring-overview.md#clientless_device_type) bij gebruik van Clientless, zodat verschillende soorten analyses kunnen worden uitgevoerd voor bijvoorbeeld Roku, AppleTV, Xbox enz.</br></br>Zie [Voordelen om de clientless parameter van het apparatentype in pasmetriek te gebruiken ](/help/authentication/benefits-of-using-the-clientless-devicetype-parameter-in-pass-metrics.md)</br></br>**Opmerking**: device_info zal deze parameter vervangen. |
| _deviceUser_ | De gebruikers-id van het apparaat.</br></br>**Opmerking**: Indien gebruikt, moet deviceUser dezelfde waarden hebben als in het dialoogvenster [Registratiecode maken](/help/authentication/registration-code-request.md) verzoek. |
| _appId_ | De toepassings-id/-naam. </br></br>**Opmerking**: device_info vervangt deze parameter. Indien gebruikt, `appId` moeten dezelfde waarden hebben als in de [Registratiecode maken](/help/authentication/registration-code-request.md) verzoek. |

>[!IMPORTANT]
> 
>De logout vraag heeft momenteel de volgende beperking: de AuthN- en AuthZ-tokens worden uit de opslag verwijderd (dus aan de zijde Programmer/Primetime-verificatie), maar **niet** roep het MVPD logout eindpunt. 


