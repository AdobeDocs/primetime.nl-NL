---
description: Als u de DASH-inhoud wilt afspelen die het resultaat is van het verpakken van inhoud, moet de TVSDK-client de coderingssleutel voor de inhoud verkrijgen die tijdens het pakketproces is doorgegeven in de workflow voor sleutelaankopen. De ontsleutelingssleutel voor de client-inhoud wordt doorgaans door een Widevine/PlayReady-licentieserver aan de client geleverd als reactie op een of meer HTTP/HTTPS-berichten van de client.
title: Overzicht van de workflow voor het aanvragen van clientsleutels
exl-id: ae600cbd-415b-441a-bf01-f259993071f2
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Workflow voor aanvragen van clientsleutels {#client-key-request-workflow-overview}

Als u de DASH-inhoud wilt afspelen die het resultaat is van het verpakken van inhoud, moet de TVSDK-client de coderingssleutel voor de inhoud verkrijgen die tijdens het pakketproces is doorgegeven in de workflow voor sleutelaankopen. De ontsleutelingssleutel voor de client-inhoud wordt doorgaans door een Widevine/PlayReady-licentieserver aan de client geleverd als reactie op een of meer HTTP/HTTPS-berichten van de client.

De PSDK-client moet het volgende doen om de coderingssleutel voor inhoud te verkrijgen

* Pak het PSE-vak van de inhoud, geef het aan het platform en verkrijg het als reactie op een sleutelverzoek.
* Verzend het zeer belangrijke verzoek uit naar de aangewezen Widevine/PlayReady vergunningsserver door een POST van HTTP.
* Geef de reactie van de server door aan het platform dat de ontsleutelingssleutel voor de client-inhoud uit de reactie zal extraheren en dit zal gebruiken voor de ontsleuteling van inhoud.

Als u de HTTP-POST voor de hoofdaanvraag wilt verzenden, moet uw code de URL van de licentieserver en eventuele extra gegevens die aan de post moeten worden gekoppeld, doorgeven aan de PSDK-client. De keuze van URL en gegevens die moeten worden doorgegeven, is afhankelijk van de WiFi/PlayReady-serviceprovider waarmee u werkt. Bijvoorbeeld, als u ExpressPlay voor het verlenen van de dienst gebruikt, gaat u in aangewezen ExpressPlay Widevine/PlayReady vergunningsserver URL over en maakt aan het uitgaande zeer belangrijke verzoek het token ExpressPlay verbonden aan de encryptiesleutel van de inhoud vast. U kunt de juiste ExpressPlay Widevine/PlayReady-licentieserver-URL ophalen vanuit de ExpressPlay-documentatie.
