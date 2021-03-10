---
title: Gebruikersverificatie
description: Gebruikersverificatie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Gebruikersverificatie {#user-authentication}

Een Adobe Primetime DRM-aanvraag kan een verificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek `AuthenticationToken` omvatten die door `AuthenticationHandler` wordt geproduceerd. Als u tot het teken toegang wilt hebben en verifiëren, moet u `RequestMessageBase.getAuthenticationToken()` gebruiken. Als u een verzoek voor een gebruikersnaam/wachtwoord wilt starten op de client, gebruikt u de ActionScript- of iOS-API van `DRMManager.authenticate()`.

Als de client en server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client via een ander kanaal een verificatietoken en wordt het aangepaste verificatietoken ingesteld met de ActionScript 3.0-API van `DRMManager.setAuthenticationToken`. Gebruik `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.
