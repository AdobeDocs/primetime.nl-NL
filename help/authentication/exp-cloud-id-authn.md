---
title: Experience Cloud-id gebruiken in Primetime-verificatie
description: Experience Cloud-id gebruiken in Primetime-verificatie
exl-id: 03354c01-5aad-4d81-beee-1c3834599134
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Experience Cloud-id gebruiken in Primetime-verificatie

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Wat is Experience Cloud-id en hoe kan ik deze verkrijgen? {#what-exp-cloud-id-obtain}

De Experience Cloud-id (ECID for short) is een unieke id die door Adobe Experience Cloud wordt gegenereerd voor elke afzonderlijke gebruiker in uw toepassing/website. ECID wordt in hoge mate gebruikt in alle rapporten van het Experience Cloud die worden gebruikt om informatie over een specifieke gebruiker in meerdere toepassingen/websites te koppelen.

Als u al een systeem hebt dat een bezoekersidentiteitskaart verstrekt, zou u zelfde identiteitskaart voor het werkingsgebied van dit document moeten gebruiken.

Een manier om de ECID te verkrijgen, is het gebruik van Experience Cloud ID Service. U kunt het gewenste implementatietype gebruiken op basis van TDM, JS-bibliotheek, server, directe integratie of native bibliotheken voor mobiele platforms. Voor een uitgebreide weergave van beschikbare services, bibliotheken, SDK&#39;s en implementatiehandleidingen, raadpleegt u: <https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html>

## Wat is het voordeel om Experience Cloud ID in Authentificatie te gebruiken Primetime? {#benefit-ex-cloud-id}

Als u onze SDK&#39;s en client REST API configureert voor gebruik van uw ECID, kunt u de gegevens die via Primetime-verificatie zijn verzameld later koppelen aan uw bestaande Experience Cloud-oplossingen. Hierdoor kunt u de reis en ervaring van uw klanten beter begrijpen voor alle oplossingen die door de Adobe worden geboden.

## Hoe te om Experience Cloud identiteitskaart in Authentificatie te gebruiken Primetime? {#how-to-ex-cloud-id-authn}

Nadat u de ECID hebt ontvangen (zie hierboven), moet u deze informatie doorgeven aan onze SDK&#39;s en onze client-less REST API. Deze informatie zal later aan onze servers op elke netwerkvraag worden overgegaan die SDK maakt. Het configuratieproces is als volgt verschillend voor elke SDK:

### JS SDK {#js-sdk}

Voor JavaScript moet u de ECID in een kaart doorgeven als de derde parameter aan de aanroep setRequestor.

**Voorbeeld van gebruik:**

```JavaScript
accessEnabler.setRequestor("REQUESTOR_ID", ["ENDPOINT_URL"],
    {
        "visitorID": "THE_ECID_VALUE"
    }
);
```

### iOS/tvOS SDK {#ios-sdk}

Voor iOS/tvOS SDK is er een speciale methode genaamd setOptions.

**Voorbeeld van gebruik:**

```JavaScript
accessEnabler.setOptions(
    [
        "visitorID": "THE_ECID_VALUE"
    ]
);
```

### Android/fireTV SDK {#android-sdk}

Voor Android/fireTV SDK is het mechanisme vergelijkbaar met iOS. Alleen de parameternaam is anders. De API wordt hier beschreven.

**Voorbeeld van gebruik:**

```JavaScript
String visitor_id = "THE_ECID_VALUE";

HashMap<String, String> options = new HashMap();
options.put("ap_vi",visitor_id);

accessEnabler.setOptions(options);
```

### Clientloze API {#clientless-api}

Als u Adobe Primetime gebruikt via de REST API, **ECID** waarde moet worden verzonden **op alle API&#39;s** als een parameter met de naam **&#39;ap_vi&#39;**.

**Voorbeeld van gebruik:**

`GET: https://api.auth.adobe.com/api/v1/authorize?...&ap_vi=THE_ECID_VALUE`
