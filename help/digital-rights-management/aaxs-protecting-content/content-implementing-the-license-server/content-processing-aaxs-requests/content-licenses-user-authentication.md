---
title: Gebruikersverificatie
description: Gebruikersverificatie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Gebruikersverificatie{#user-authentication}

Een verzoek van de Toegang van Adobe kan een authentificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek `AuthenticationToken` bevatten die door `AuthenticationHandler` wordt geproduceerd. Om tot het teken toegang te hebben en te verifiëren, gebruik `RequestMessageBase.getAuthenticationToken()`. Als u een verzoek voor een gebruikersnaam/wachtwoord wilt starten op de client, gebruikt u de ActionScript- of iOS-API van `DRMManager.authenticate()`.

Als de client en de server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client via een ander kanaal een verificatietoken en wordt het aangepaste verificatietoken ingesteld met behulp van de `DRMManager.setAuthenticationToken` ActionScript 3.0-API. Gebruik `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.
