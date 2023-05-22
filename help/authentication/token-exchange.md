---
title: Uitwisseling een teken van Platform SSO voor een teken van Adobe
description: Uitwisseling een teken van Platform SSO voor een teken van Adobe
exl-id: 5ab60268-8f97-4755-8281-be45e812ed7f
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 2%

---

# Uitwisseling een teken van Platform SSO voor een teken van Adobe {#exchange-a-platform-sso-token-for-an-adobe-token}

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

Staat toe dat een Platform SSO-profiel wordt &quot;uitgewisseld&quot; voor een Adobe-token.

| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/authoring | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager (verplicht)</br>    </br>2.  deviceId (verplicht)</br>    </br>3.  mvpd (verplicht)</br>    </br>4.  deviceType (verplicht)</br>    </br>5.  SAMLResponse (verplicht)</br>    </br>6.  deviceUser (Afgekeurd)</br>    </br>7.  appId (afgekeurd) | POST | De succesvolle reactie zal 204 Geen Inhoud zijn, erop wijzend dat het teken met succes werd gecreeerd en klaar voor gebruik voor de auteurstromen is. | 204 - Geen inhoud   </br>400 - Onjuist verzoek |


| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| deviceId | De id-bytes van het apparaat. |
| mvpd | De MVPD-id waarvoor deze bewerking geldig is. |
| deviceType | Het Apple-platform waarvoor we een aanvraag voor een profiel proberen te verkrijgen.  Willekeurig **iOS** of **tvOS**. |
| SAMLResponse | Het werkelijke profiel zoals geretourneerd door Platform SSO. |
| _deviceUser_ | De gebruikers-id van het apparaat. |
| _appId_ | De toepassings-id/-naam. |
