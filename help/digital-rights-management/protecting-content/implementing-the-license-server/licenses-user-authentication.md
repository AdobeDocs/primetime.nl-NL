---
seo-title: Gebruikersverificatie
title: Gebruikersverificatie
uuid: 5cbd76b9-ff64-4a4b-8cfd-54f05c04eaa3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Gebruikersverificatie {#user-authentication}

Een Adobe Primetime DRM-aanvraag kan een verificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek `AuthenticationToken` omvatten die door `AuthenticationHandler` wordt geproduceerd. Als u tot het teken toegang wilt hebben en verifiëren, moet u `RequestMessageBase.getAuthenticationToken()` gebruiken. Als u een verzoek voor een gebruikersnaam/wachtwoord wilt starten op de client, gebruikt u de ActionScript- of iOS-API van `DRMManager.authenticate()`.

Als de client en server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client via een ander kanaal een verificatietoken en wordt het aangepaste verificatietoken ingesteld met de ActionScript 3.0-API van `DRMManager.setAuthenticationToken`. Gebruik `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.
