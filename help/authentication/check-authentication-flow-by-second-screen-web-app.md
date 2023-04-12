---
title: Verificatiestroom controleren op tweede scherm van webtoepassing
description: Verificatiestroom controleren op tweede scherm van webtoepassing
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Verificatiestroom controleren op tweede scherm van webtoepassing {#check-authentication-flow-by-second-screen-web-app}

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

Deze API moet worden gebruikt door de tweede webtoepassing voor schermaanmelding om te bevestigen dat Adobe Primetime-verificatie heeft bevestigd dat MVPD met succes is aangemeld. Wij adviseren roepend deze API alvorens een succesbericht aan het eind te tonen - gebruiker die hem/haar instrueert om aan de apparatenconsole te werk te gaan om met de werkschema&#39;s verder te gaan.


| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| SP_FQDN/api/v1/checkauther/{registration code} | Aanmeldingswebtoepassing | 1. registratiecode  </br>    (component Path)</br>2.  aanvrager  </br>    (Verplicht) | GET | XML of JSON met foutdetails als dit mislukt. | 200 - Succes   </br>403 - Verboden |

</br>

| Invoerparameter | Beschrijving |
| ----------------- | --------------------------------------------------------------------------------------------- |
| registratiecode | De waarde van de registratiecode die door de gebruiker aan het begin van de authentificatiestroom wordt verstrekt. |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |


### Samplereactie (in geval van een fout) {#response}

```JSON
    {
        "status": 403,
        "message": "Forbidden"
    }
```

### [Terug naar REST API-naslaggids](/help/authentication/rest-api-reference.md)
