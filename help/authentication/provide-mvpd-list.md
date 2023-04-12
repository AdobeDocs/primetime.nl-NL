---
title: MVPD-lijst opgeven
description: MVPD-lijst opgeven
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# MVPD-lijst opgeven {#provide-mvpd-list}

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

Keert lijst van gevormde MVPDs voor de aanvrager terug.

| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/config/{requestId}</br></br>Bijvoorbeeld:</br></br>&lt;sp_fqdn>/api/v1/config/sampleRequestorId | Primetime-verificatie | 1. Aanvrager</br>    (component Path)</br>_2.  deviceType (afgekeurd)_ | GET | XML of JSON met lijst van MVPD&#39;s. | 200 |

{style="table-layout:auto"}


| Invoerparameter | Beschrijving |
| --------------- | ------------------------------------------------------------- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| *deviceType* | Apparaattype. |

{style="table-layout:auto"}

### Samplereactie {#sample-response}

Hetzelfde als de bestaande Reactie van XML MVPD op /config servlet

Opmerking: Alle MVPDs die wordt gevormd om gebruik van Platform SSO te maken zal de volgende extra eigenschappen binnen hun overeenkomstige knoop (JSON/XML) hebben:

* **enablePlatformServices (boolean):** markering die aangeeft of deze MVPD is geïntegreerd via Platform SSO
* **boardingStatus (tekenreeks):** markering die aangeeft of de MVPD Platform SSO volledig ondersteunt (ONDERSTEUND) of dat de MVPD alleen wordt weergegeven in de platformkiezer (PICKER)
* **displayInPlatformPicker (Boolean):** moet deze MVPD worden weergegeven in de platformkiezer
* **platformMappingId (tekenreeks):** de identificatiecode van deze MVPD zoals bekend door het platform
* **requiredMetadataFields (array string):** de velden met gebruikersmetagegevens die naar verwachting beschikbaar zijn bij een geslaagde aanmelding
