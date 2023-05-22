---
title: SSO-profielaanvraag van Platform ophalen
description: SSO-profielaanvraag van Platform ophalen
exl-id: 44fd4e26-4d9a-4607-ac2c-b85d848f5fc6
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# SSO-profielaanvraag van Platform ophalen {#retrieve-platform-sso-profile-request}

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

Deze bron produceert profielaanvragen voor een aanvraag-id en een MVPD-bestand.


| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/{request}/profile-Requests/{mvpd} | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager (padparam)</br>2. mvpd (padparam)</br>3. deviceType (verplicht) | GET | Het antwoord Content-Type is application/octet-stream, omdat de werkelijke lading ondoorzichtig is voor de clienttoepassing.</br></br>Het antwoord moet door de aanvraag aan het Platform worden toegezonden</br></br>SSO-engine voor het verkrijgen van een profiel-SSO. | 200 - Succes   </br>400 - Onjuist verzoek |


| Invoerparameter | Beschrijving |
| --------------- | -------------------------------------------------------------------------------------------------------- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| mvpd | De MVPD-id waarvoor deze bewerking geldig is. |
| deviceType | Het Apple-platform waarvoor we een aanvraag voor een profiel proberen te verkrijgen.  Willekeurig **iOS** of **tvOS**. |
