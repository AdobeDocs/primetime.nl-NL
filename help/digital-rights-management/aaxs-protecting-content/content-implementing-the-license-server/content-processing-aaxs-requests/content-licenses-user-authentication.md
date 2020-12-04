---
seo-title: Gebruikersverificatie
title: Gebruikersverificatie
uuid: 191964eb-cd68-47a6-8214-aec01f993df4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Gebruikersverificatie{#user-authentication}

Een verzoek van de Toegang van Adobe kan een authentificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek `AuthenticationToken` bevatten die door `AuthenticationHandler` wordt geproduceerd. Om tot het teken toegang te hebben en te verifiëren, gebruik `RequestMessageBase.getAuthenticationToken()`. Als u een verzoek voor een gebruikersnaam/wachtwoord wilt starten op de client, gebruikt u de ActionScript- of iOS-API van `DRMManager.authenticate()`.

Als de client en de server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client via een ander kanaal een verificatietoken en wordt het aangepaste verificatietoken ingesteld met behulp van de `DRMManager.setAuthenticationToken` ActionScript 3.0-API. Gebruik `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.
