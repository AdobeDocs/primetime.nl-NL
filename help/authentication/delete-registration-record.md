---
title: Registratierecord verwijderen
description: Registratieresord verwijderen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Registratierecord verwijderen {#delete-registration-record}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## REST API-eindpunten {#clientless-endpoints}

&lt;reggie_fqdn>:

* Productie - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Productie - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>


## Beschrijving {#delete-record}

Verwijdert de reg code-record en geeft de reg-code vrij voor hergebruik.

| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;reggie_fqdn>/reggie/v1/{requestorId}/regcode/{registrationCode}</br></br>Bijvoorbeeld:</br></br>&lt;reggie_fqdn>/reggie/v1/regcode/ER45RTY | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. ID aanvrager  </br>    (component Path)</br>2.  Registratiecode  </br>    (component Path) | DELETE | Geen | 204 |

{style="table-layout:auto"}

</br>

| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| registratiecode | De waarde van de registratiecode die op het Streaming Apparaat (dat in de authentificatiestroom moet worden ingegaan) zou worden getoond. |

{style="table-layout:auto"}

</br>

### [Terug naar REST API Reference](/help/authentication/rest-api-reference.md)
