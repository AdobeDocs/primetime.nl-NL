---
seo-title: Overzicht
title: Overzicht
uuid: 870c32f5-1119-4fec-abed-25e51dd1ebe3
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Overzicht{#overview}

De algemene benadering van het behandelen van verzoeken is een manager tot stand te brengen, het verzoek te ontleden, de reactiegegevens of foutencode te plaatsen, en de manager te sluiten.

De basisklasse die wordt gebruikt om enige verzoek/reactieinteractie te behandelen is `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Een instantie van de klasse `HandlerConfiguration` wordt gebruikt om de manager te initialiseren. `HandlerConfiguration` slaat de informatie van de serverconfiguratie, met inbegrip van vervoergeloofsbrieven, timestamp tolerantie, de lijsten van de beleidsupdate, en herroepingslijsten op.De manager leest de verzoekgegevens en ontleedt het verzoek in een geval van  `RequestMessageBase`. De aanroeper kan de informatie in het verzoek onderzoeken en beslissen of om een fout of een succesvolle reactie (subklassen van `RequestMessageBase` verstrekken een methode om reactiegegevens te plaatsen) terug te keren.

Als het verzoek succesvol is, stelt u de reactiegegevens in. anders `RequestMessageBase.setErrorData()` aanhalen bij mislukking. Beëindig altijd de implementatie door de `close()` methode aan te roepen (het wordt geadviseerd dat `close()` in het `finally` blok van een `try` verklaring wordt geroepen). Zie de `MessageHandlerBase` API verwijzingsdocumentatie voor een voorbeeld van hoe te om de manager aan te halen.

>[!NOTE]
>
>HTTP-statuscode 200 (OK) moet worden verzonden als reactie op alle aanvragen die door de handler worden verwerkt. Als de handler niet kon worden gemaakt vanwege een serverfout, reageert de server mogelijk met een andere statuscode, zoals 500 (Interne serverfout).

De client gebruikt de licentieserver-URL die tijdens het verpakken is opgegeven als de basis-URL voor alle aanvragen die naar de licentieserver worden verzonden. Als de server-URL bijvoorbeeld is opgegeven als &quot;ht<span></span>tps://licenseserver.com/path&quot;, verzendt de client aanvragen naar &quot;ht<span></span>tps://licenseserver.com/path/flashaccess/...&quot;. Zie de volgende secties voor details over de specifieke weg die voor elk type van verzoek wordt gebruikt. Wanneer u uw licentieserver implementeert, moet u ervoor zorgen dat de server reageert op de paden die voor elk type aanvraag zijn vereist.

Een licentieaanvraag kan een verificatietoken bevatten. Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek `AuthenticationToken` bevatten die door `AuthenticationHandler` wordt geproduceerd, en SDK zal ervoor zorgen het teken geldig is alvorens een vergunning uit te geven.
