---
description: Gebruik het bevel van de GET van HTTP om met de manifestserver in wisselwerking te staan.
seo-description: Gebruik het bevel van de GET van HTTP om met de manifestserver in wisselwerking te staan.
seo-title: Een opdracht naar de manifest-server verzenden
title: Een opdracht naar de manifest-server verzenden
uuid: e9680563-d268-406d-87ce-1521a677e9ec
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Een opdracht naar de manifest-server verzenden {#send-a-command-to-the-manifest-server}

Gebruik het bevel van de GET van HTTP om met de manifestserver in wisselwerking te staan.

1. Verzend een `HTTP GET` verzoek om een laarzentrekker URL die met het volgende patroon wordt samengesteld:

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.m3u8
    ?{query parameters}
   ```

* **** PublisherAssetIDR vereist. De unieke id van de uitgever voor de specifieke inhoud.

* **Inhoud** URLRequired. URL van de inhoud van het M3U8-bestand, Base64-gecodeerd om veilig te zijn binnen de URL van de manifestserver. De inhoud-URL moet verwijzen naar een M3U8-bestand van een andere type, zelfs als er slechts één bitsnelheidstream is.

* **Query-** parametersSommige zijn vereist, sommige zijn optioneel. Deze vormen het meest gevarieerde deel van het verzoek. Zij vertellen de duidelijke server welke soort cliënt het verzoek doet en wat het de manifestserver wil doen.

   Bijvoorbeeld:

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.m3u8?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTP- vs. HTTPS-aanvragen**

   De manifestserver leidt tot URLs gebruikend het zelfde protocol van HTTP van het verzoek van de cliënt. Wanneer een speler een niet-beveiligd HTTP-verzoek (http) indient, retourneert de manifestserver manifest-URL&#39;s en URL&#39;s voor bijhouden van bestandsgrootte met het http-protocol. Als een speler een beveiligde HTTP-verbinding (https) maakt, geeft de manifestserver duidelijke URL&#39;s en URL&#39;s van Auditude tracking met het https-protocol.

   >[!NOTE]
   >
   >De manifestserver kan het protocol (HTTP of HTTPS) van inhoudssegmenten (.ts) en derde partij het volgen beacons niet veranderen. U moet contact opnemen met de inhoud en externe advertentieproviders om ervoor te zorgen dat deze de gewenste protocollen configureren.