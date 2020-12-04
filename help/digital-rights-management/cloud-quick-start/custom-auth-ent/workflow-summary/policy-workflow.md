---
seo-title: Details van beleidswerkstroom
title: Details van beleidswerkstroom
uuid: b355fcf6-3416-440f-9b30-a155e20f9f74
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---


# BES-workflow {#bees-workflow}

**Overzicht:**

* **Beleid**  - creeer een DRM BEES-bewust beleid dat wijst op BES voor alle inhoud wordt vereist die met dit beleid wordt verpakt.
* **Verpakken**  - Inhoud verpakken met gebruik van het DRM-beleid dat BEES-compatibel is.
* **Verificatie**  - Verifieer uw clientapparaat en gebruik de Primetime DRM-API of de Primetime-API om dit token te koppelen aan Primetime Cloud DRM. Als u dit doet, stuurt het clientapparaat dit verificatietoken samen met alle licentieaanvragen naar Primetime Cloud DRM. Met Primetime Cloud DRM wordt dit token niet verwerkt, maar wordt het doorgegeven (als een ondoorzichtig blok) aan het BES-eindpunt voor verwerking.
* **Licentie**  - Vraag een licentie aan voor uw beveiligde inhoud. Het cliëntapparaat zal automatisch uw eerder-vastgestelde authentificatietoken aan de vraag toevoegen.
* **Entitlement**  - Primetime Cloud DRM bepaalt of de inhoud is verpakt met een beleid waarvoor BES vereist is. Met Primetime Cloud DRM wordt een JSON-aanvraag gemaakt voor verzending naar het BES-eindpunt. In de reactie van de BES wordt Primetime Cloud DRM geïnstrueerd of een licentie moet worden uitgegeven of niet, en optioneel welk DRM-beleid moet worden gebruikt.

## Details van beleidswerkstroom {#policy-workflow-details}

Wanneer Primetime Cloud DRM een vergunningsverzoek verwerkt, ontleedt het het beleid DRM in het verzoek om te bepalen als een vraag aan de backend-machtigingsdienst wordt vereist alvorens de inhoud kan worden getoond. Als een vraag van BES *is* vereist, zal de Ouderwetse DRM tot het verzoek van BES leiden, dan ontleedt het DRM beleid om een gespecificeerd eindpunt van BES URL voor het verzoek van BES te verkrijgen.

Pas uw beleid DRM toe dat op het vereiste BES wijst, die de volgende twee douaneeigenschappen in het beleid specificeren:

    * &quot;policy.customProp.1=bees.required=&lt;true>&quot;
    * ` policy.customProp.2=bees.url=&lt;url to=&quot;&quot; your=&quot;&quot; BEES=&quot;&quot; endpoint=&quot;&quot;>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

Als u bijvoorbeeld Primetime DRM-beleidsbeheer gebruikt ( [!DNL AdobePolicyManager.jar]), geeft u de volgende twee aangepaste eigenschappen op in het configuratiebestand [!DNL flashaccesstools.properties]:

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>Als u `policy.customProp.1` of `policy.customProp.2` voor een andere bezit reeds gebruikt, gebruik eenvoudig unieke aantallen voor de nieuwere eigenschappen.

## Details van de pakketworkflow {#package-workflow-details}

Tijdens het verpakken van uw Adobe Access-beveiligde inhoud moet u een van uw DRM-beleid met BEES-vermogen toepassen op de inhoud.

## Gegevens verificatieworkflow {#authentication-workflow-details}

Opdat uw eindpunt BEES machtigingsbesluiten kan nemen, moet het cliëntapparaat authentificatieinformatie verstrekken. U verwezenlijkt dit door uw eigen klant-specifiek authentificatietoken te gebruiken.

Primetime Cloud DRM hoeft deze token niet te begrijpen, maar geeft deze token door aan het eindpunt van uw BES. Het clientapparaat is verantwoordelijk voor het maken of ophalen van dit token en het instellen ervan met de API `DRMManager.setAuthenticationToken()`.

Ga als volgt te werk om deze token te koppelen aan Primetime Cloud DRM, zodat deze wordt verzonden met de licentieaanvraag:

Instantieer het `DRMManager`-object met de DRM-metagegevens van de inhoud die is verpakt voor Primetime Cloud DRM.

De methode `setAuthenticationToken()` werkt door de opgegeven bytearray te koppelen aan de URL van de licentieserver in de DRM-metagegevens die is gebruikt om `DRMManager` te instantiëren.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

Het teken wordt verzonden met alle vergunningsverzoeken tot het teken door `.setAuthenticationToken` met ongeldig als parameter te roepen wordt ontruimd.

## Informatie over licentieworkflow{#license-workflow-details}

Vraag een licentie aan via Primetime Cloud DRM door `mgr.loadVoucher()` aan te roepen.

## Entitlement request and response details{#entitlement-request-and-response-details}

Wanneer Primetime Cloud DRM bepaalt dat de inhoud met een BES-bewust DRM beleid werd verpakt, bouwt het het volgende JSON- verzoek om naar het BEES eindpunt te verzenden dat in het DRM beleid wordt gespecificeerd:

```
{
    "title":"Entitlement Request",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"Unique ID for this message. Used to confirm that the
                           returned response is for this particular message."
        },
        "version": {
            "type":"string",
            "description":"BEES Request Version. Currently 1."
        },
        "contentID": {
            "type":"string",
            "description":"Content ID (GUID)"
        },
        "customerSpecificAuthToken": {
            "type":"string",
            "description":"Base64-encoded authentication token. Must be set
                           explicitly by client before making the license request."
        }
    },
    "required": [
        "messageID",
        "version",
        "contentID"
    ]
}
```

De volgende respons wordt verwacht van het BES-eindpunt:

```
{
    "title":"Entitlement Response",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"ID of the Entitlement Request that this Response is
                           handling. Must exactly match the ID of the request
                           or this response will be rejected."
        },
        "version": {
            "type":"string",
            "description":"BEES Response Version. Currently 1."
        },
        "isAllowed": {
            "type":"boolean",
            "description":"Grant the license or not."
        },
        "policy": {
            "type":"string",
            "description":"Base64-encoded policy to enforce  If no policy is
                           provided, the policy that was packaged with the content
                           during packaging time will be used to generate the license."
        },
        "error": {
            "type":"integer",
            "description":"An error number produced by the entitlement server.
                           Will be passed to the client as the 'code' field of
                           the server error response."
        },
        "errorText": {
            "type":"string",
            "description":"Additional error information produced by the
                           entitlement server. Will be passed to the client as
                           the 'text' field of the server error response."
        }
    },
    "required": [
        "messageID",
        "version",
        "isAllowed"
    ]
}
```

Primetime Cloud DRM gebruikt het antwoord om te bepalen of het een vergunning aan het verzoekende apparaat al dan niet zou moeten uitgeven, en of het een nieuw beleid DRM in het proces van de vergunningsgeneratie zou moeten vervangen. Als `isAllowed` `true` is en geen beleid in de reactie wordt verstrekt, dan zal het originele DRM Beleid dat tijdens de tijd van de inhoudspakketverpakking wordt gebruikt worden gebruikt om de vergunning te produceren.