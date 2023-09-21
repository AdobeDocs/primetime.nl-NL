---
title: Overzicht
description: Overzicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Overzicht{#overview}

De algemene benadering van het behandelen van verzoeken is een manager tot stand te brengen, het verzoek te ontleden, de reactiegegevens of foutencode te plaatsen, en de manager te sluiten.

De basisklasse die wordt gebruikt voor het verwerken van interactie met een enkele aanvraag/reactie is `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Een instantie van de `HandlerConfiguration` wordt gebruikt om de handler te initialiseren. `HandlerConfiguration` slaat de informatie van de serverconfiguratie, met inbegrip van vervoergeloofsbrieven, timestamp tolerantie, de lijsten van de beleidsupdate, en herroepingslijsten op.De manager leest de verzoekgegevens en ontleedt het verzoek in een geval van `RequestMessageBase`. De aanroeper kan de informatie in het verzoek onderzoeken en beslissen of een fout of een succesvolle reactie (subklassen van `RequestMessageBase` een methode opgeven voor het instellen van reactiegegevens).

Als het verzoek succesvol is, plaats de reactiegegevens; anders aanhalen `RequestMessageBase.setErrorData()` bij mislukking. Beëindig altijd de implementatie door het `close()` methode (aanbevolen wordt `close()` worden opgeroepen in het `finally` blok van een `try` instructie). Zie de `MessageHandlerBase` API verwijzingsdocumentatie voor een voorbeeld van hoe te om de manager aan te halen.

>[!NOTE]
>
>HTTP-statuscode 200 (OK) moet worden verzonden als reactie op alle aanvragen die door de handler worden verwerkt. Als de handler niet kon worden gemaakt vanwege een serverfout, reageert de server mogelijk met een andere statuscode, zoals 500 (Interne serverfout).

De client gebruikt de licentieserver-URL die tijdens het verpakken is opgegeven als de basis-URL voor alle aanvragen die naar de licentieserver worden verzonden. Als de server-URL bijvoorbeeld wordt opgegeven als &quot;ht<span></span>tps://licenseserver.com/path&quot;, verzendt de client aanvragen naar &quot;ht<span></span>tps://licenseserver.com/path/flashaccess/...&quot; Zie de volgende secties voor details over de specifieke weg die voor elk type van verzoek wordt gebruikt. Wanneer u uw licentieserver implementeert, moet u ervoor zorgen dat de server reageert op de paden die voor elk type aanvraag zijn vereist.

Een licentieaanvraag kan een verificatietoken bevatten. Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek een `AuthenticationToken` door de `AuthenticationHandler`en de SDK zorgt ervoor dat de token geldig is voordat een licentie wordt uitgegeven.
