---
title: Metagegevens gebruiker
description: Metagegevens gebruiker
exl-id: 3d7b6429-972f-4ccb-80fd-a99870a02f65
source-git-commit: 4479df7985da16e8632a538f1042de05109f2392
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Metagegevens gebruiker {#user-metadata}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## REST API-eindpunten {#clientless-endpoints}

`<REGGIE_FQDN>`:

* Productie - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

`<SP_FQDN>`:

* Productie - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Staging - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>

## Beschrijving {#description}

Haal meta-gegevens terug die MVPD over de voor authentiek verklaarde gebruiker deelde.


| Endpoint | Geroepen  </br>Door | Invoer   </br>Params | HTTP  </br>Methode | Antwoord | HTTP  </br>Antwoord |
| --- | --- | --- | --- | --- | --- |
| `<SP_FQDN>`/api/v1/tokens/usermetadata | Streaming-app</br></br>of</br></br>Programmeringsservice | 1. aanvrager</br>2.  deviceId (verplicht)</br>3.  device_info/X-Device-Info (verplicht)</br>4.  deviceType</br>5.  deviceUser (Afgekeurd)</br>6.  appId (afgekeurd) | GET | XML of JSON bevatten gebruikersmetagegevens of foutgegevens als dit niet lukt. | 200 - Succes<p>404 - Geen metagegevens gevonden<p>412 - Ongeldige token AuthN (bijvoorbeeld verlopen token) |


| Invoerparameter | Beschrijving |
| --- | --- |
| aanvrager | De programmeeraanvragerId waarvoor deze verrichting geldig is. |
| deviceId | Het apparaat-id bytes. |
| device_info/<p>X-Apparaat-Info | Informatie over streaming apparaat.<p>**Opmerking**: This MAY BE passed device_info as a URL parameter, but due to the potential size of this parameter and constraints on the length of a GET URL, it should be passed as X-Device-Info in the http header. </br></br>Zie de volledige details in **Gegevens van apparaat en verbinding doorgeven** <!--http://tve.helpdocsonline.com/passing-device-information-->. |
| _deviceType_ | Het apparaattype (bijvoorbeeld Roku, PC).<p>Als deze parameter correct is ingesteld, biedt ESM metriek die [uitgesplitst per apparaattype](/help/authentication/entitlement-service-monitoring-overview.md#progr-filter-metrics) bij gebruik van Clientless, zodat verschillende soorten analyses kunnen worden uitgevoerd voor bijvoorbeeld Roku, AppleTV, Xbox enz.<p>Zie [Voordelen van het gebruiken van clientless apparatentype parameter in de Gegevens van de Pas](/help/authentication/benefits-of-using-the-clientless-devicetype-parameter-in-pass-metrics.md)<p>**Opmerking:** De `device_info` vervangt deze parameter. |
| _deviceUser_ | De gebruikers-id van het apparaat.</br></br>**Opmerking:**Indien gebruikt, `deviceUser` moeten dezelfde waarden hebben als in de [Registratiecode maken](/help/authentication/registration-code-request.md) verzoek. |
| _appId_ | De toepassings-id/-naam. <p>**Opmerking:**De `device_info` vervangt deze parameter. Indien gebruikt, `appId` moeten dezelfde waarden hebben als in de **Registratiecode maken** verzoek. |

>[!NOTE]
> 
>De informatie van gebruikersmeta-gegevens zou beschikbaar moeten zijn nadat de authentificatiestroom heeft voltooid, maar kan op de vergunningsstroom, afhankelijk van MVPD en op het meta-gegevenstype worden bijgewerkt.




## Samplereactie {#sample-response}

Na een geslaagde aanroep zal de server reageren met een XML- (standaard) of JSON-object met een structuur die vergelijkbaar is met de hieronder weergegeven structuur:


```JSON
    {
        updated: 1334243471,
        encrypted: ["encryptedProp"],
        data: {
              zip: ["12345", "34567"],
              maxRating: { 
                  "MPAA": "PG-13",
                  "VCHIP": "TV-Y", 
                  "URL": "http://exam.pl/e/manage/ratings"
                         },
              householdID: "3456",
              userID: "BgSdasfsdk23/dsaf3+saASesadgfsShggssd=",
              channelID: ["channel-1", "channel-2"]
              }
    }
```

Aan de basis van het object bevinden zich drie knooppunten:

* **bijgewerkt**: geeft een UNIX-tijdstempel op die de laatste keer vertegenwoordigt dat de metagegevens zijn bijgewerkt. Dit bezit zal aanvankelijk door de server worden geplaatst wanneer het produceren van de meta-gegevens tijdens de authentificatiefase. Volgende aanroepen (nadat de metagegevens zijn bijgewerkt) resulteren in een verhoogde tijdstempel.
* **data**: bevat de werkelijke metagegevenswaarden.
* **gecodeerd**: een array met de gecodeerde eigenschappen. Om een specifieke meta-gegevenswaarde te decrypteren, moet de programmeur een Base64 decoderen op de meta-gegevens dan toepassen een decryptie van RSA op de resulterende waarde, gebruikend het eigen privé sleutel (de Adobe codeert de meta-gegevens op de server gebruikend het openbare certificaat van de Programmer).

Bij een fout retourneert de server een XML- of JSON-object dat een gedetailleerd foutbericht opgeeft.

Zie voor meer informatie [Metagegevens gebruiker](/help/authentication/user-metadata-feature.md).

[Terug naar REST API Reference](/help/authentication/rest-api-reference.md)
