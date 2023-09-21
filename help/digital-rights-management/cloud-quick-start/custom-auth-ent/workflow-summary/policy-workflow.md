---
title: Details van beleidswerkstroom
description: Details van beleidswerkstroom
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# BES-workflow {#bees-workflow}

**Samenvatting:**

* **Beleid** - Maak een DRM BES-bewust beleid dat aangeeft dat BES vereist is voor alle inhoud die met dit beleid is verpakt.
* **Verpakken** - Inhoud verpakken met gebruik van het DRM-beleid dat BEES-compatibel is.
* **Verificatie** - Verifieer uw clientapparaat en gebruik de Primetime DRM-API of de Primetime-API om dit token te koppelen aan Primetime Cloud DRM. Als u dit doet, stuurt het clientapparaat dit verificatietoken samen met alle licentieaanvragen naar Primetime Cloud DRM. Met Primetime Cloud DRM wordt dit token niet verwerkt, maar wordt het doorgegeven (als een ondoorzichtig blok) aan het BES-eindpunt voor verwerking.
* **Licentie** - Vraag een licentie aan voor uw beveiligde inhoud. Het cliëntapparaat zal automatisch uw eerder-vastgestelde authentificatietoken aan de vraag toevoegen.
* **Entitlement** - Met Primetime Cloud DRM wordt bepaald dat de inhoud is verpakt met een beleid waarvoor BES is vereist. Met Primetime Cloud DRM wordt een JSON-aanvraag gemaakt voor verzending naar het BES-eindpunt. In de reactie van de BES wordt Primetime Cloud DRM geïnstrueerd of een licentie moet worden uitgegeven of niet, en optioneel welk DRM-beleid moet worden gebruikt.

## Details van beleidswerkstroom {#policy-workflow-details}

Wanneer Primetime Cloud DRM een vergunningsverzoek verwerkt, ontleedt het het beleid DRM in het verzoek om te bepalen als een vraag aan de backend-machtigingsdienst wordt vereist alvorens de inhoud kan worden getoond. Als een BEES-gesprek *is* vereist, maakt Primetime Cloud DRM het BEES-verzoek en parseert vervolgens het DRM-beleid om een opgegeven BES URL-eindpunt voor het BES-verzoek te verkrijgen.

Pas uw beleid DRM toe dat op het vereiste BES wijst, die de volgende twee douaneeigenschappen in het beleid specificeren:

* `policy.customProp.1=bees.required=<true | false>`
* `policy.customProp.2=bees.url=<url to your BEES endpoint>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

Bijvoorbeeld het gebruiken van de Manager van het Beleid Primetime DRM ( [!DNL AdobePolicyManager.jar]), kunt u de volgende twee aangepaste eigenschappen opgeven in het dialoogvenster [!DNL flashaccesstools.properties] configuratiebestand:

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>Als u al `policy.customProp.1` of `policy.customProp.2` voor een andere eigenschap gebruikt u gewoon unieke getallen voor de nieuwere eigenschappen.

## Werkstroomgegevens pakket {#package-workflow-details}

Tijdens het verpakken van uw Adobe Toegang-beschermde inhoud, moet u één van uw BEES-bewuste beleid DRM op de inhoud toepassen.

## Gegevens verificatieworkflow {#authentication-workflow-details}

Opdat uw eindpunt BEES machtigingsbesluiten kan nemen, moet het cliëntapparaat authentificatieinformatie verstrekken. U verwezenlijkt dit door uw eigen klant-specifiek authentificatietoken te gebruiken.

Primetime Cloud DRM hoeft deze token niet te begrijpen, maar geeft deze token door aan het eindpunt van uw BES. Het clientapparaat is verantwoordelijk voor het maken of ophalen van dit token en het instellen ervan met de `DRMManager.setAuthenticationToken()` API.

Ga als volgt te werk om deze token te koppelen aan Primetime Cloud DRM, zodat deze wordt verzonden met de licentieaanvraag:

Instantiëren van de `DRMManager` -object met de DRM-metagegevens van de inhoud die is verpakt voor Primetime Cloud DRM.

De `setAuthenticationToken()` methode werkt door de opgegeven bytearray te koppelen aan de URL van de licentieserver die is opgegeven in de DRM-metagegevens die zijn gebruikt om een instantie te maken `DRMManager`.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

Het token wordt verzonden met alle licentieaanvragen totdat het token wordt gewist door het aanroepen `.setAuthenticationToken` met null als parameter.

## Licentieworkflowdetails{#license-workflow-details}

Vraag een licentie aan via Primetime Cloud DRM door `mgr.loadVoucher()`.

## Machtigingsverzoek en reactiegegevens{#entitlement-request-and-response-details}

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

Primetime Cloud DRM gebruikt het antwoord om te bepalen of het een vergunning aan het verzoekende apparaat al dan niet zou moeten uitgeven, en of het een nieuw beleid DRM in het proces van de vergunningsgeneratie zou moeten vervangen. Indien `isAllowed` is `true` en er is geen beleid opgegeven in het antwoord, wordt het oorspronkelijke DRM-beleid dat tijdens de tijd van het verpakken van inhoud wordt gebruikt, gebruikt om de licentie te genereren.
