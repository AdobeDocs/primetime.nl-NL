---
description: Gebruik het bevel van de GET van HTTP om met de manifestserver in wisselwerking te staan.
title: Een opdracht naar de manifest-server verzenden
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Een opdracht naar de manifest-server verzenden {#send-a-command-to-the-manifest-server}

Gebruik het bevel van de GET van HTTP om met de manifestserver in wisselwerking te staan.

1. Een `HTTP GET` request for a bootstrap URL construeert using the following pattern:

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.m3u8
    ?{query parameters}
   ```

* **PublisherAssetID** Vereist. De unieke id van de uitgever voor de specifieke inhoud.

* **Inhoud-URL** Vereist. URL van de inhoud van het M3U8-bestand, Base64-gecodeerd om veilig te zijn binnen de URL van de manifestserver. De inhoud-URL moet verwijzen naar een M3U8-bestand van een andere type, zelfs als er slechts één bitsnelheidstream is.

* **Parameters query** Sommige zijn vereist, sommige facultatief. Deze vormen het meest gevarieerde deel van het verzoek. Zij vertellen de duidelijke server welke soort cliënt het verzoek doet en wat het de manifestserver wil doen.

   Bijvoorbeeld:

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.m3u8?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTP- vs. HTTPS-aanvragen**

   De manifestserver leidt tot URLs gebruikend het zelfde protocol van HTTP van het verzoek van de cliënt. Als een speler een niet-veilig HTTP-verzoek (http) indient, retourneert de manifestserver manifest-URL&#39;s en Auditude-URL&#39;s met het http-protocol. Als een speler een beveiligde HTTP-verbinding (https) maakt, geeft de manifestserver duidelijke URL&#39;s en URL&#39;s van Auditude tracking met het https-protocol.

   >[!NOTE]
   >
   >De manifestserver kan het protocol (HTTP of HTTPS) van inhoudssegmenten (.ts) en derde partij het volgen beacons niet veranderen. U moet contact opnemen met de inhoud en externe advertentieproviders om ervoor te zorgen dat deze de gewenste protocollen configureren.