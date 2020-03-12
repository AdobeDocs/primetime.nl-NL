---
seo-title: Gebruikersverificatie
title: Gebruikersverificatie
uuid: 5cbd76b9-ff64-4a4b-8cfd-54f05c04eaa3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gebruikersverificatie {#user-authentication}

Een Adobe Primetime DRM-aanvraag kan een verificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek een `AuthenticationToken` geproduceerd door `AuthenticationHandler`. Als u tot het token toegang wilt hebben en het wilt verifiëren, moet u het gebruiken `RequestMessageBase.getAuthenticationToken()`. Gebruik de `DRMManager.authenticate()` ActionScript- of iOS-API om een aanvraag voor een gebruikersnaam/wachtwoord op de client te starten.

Als de client en server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client via een ander kanaal een verificatietoken en wordt het aangepaste verificatietoken ingesteld met behulp van de `DRMManager.setAuthenticationToken` ActionScript 3.0-API. Gebruik deze optie `RequestMessageBase.getRawAuthenticationToken()` om het aangepaste verificatietoken op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.
