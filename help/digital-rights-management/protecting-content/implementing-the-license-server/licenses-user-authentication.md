---
title: Gebruikersverificatie
description: Gebruikersverificatie
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Gebruikersverificatie {#user-authentication}

Een Adobe Primetime DRM-aanvraag kan een verificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek omvatten `AuthenticationToken` door de `AuthenticationHandler`. Als u tot het token toegang wilt hebben en het wilt verifiëren, moet u `RequestMessageBase.getAuthenticationToken()`. Als u een aanvraag voor een gebruikersnaam/wachtwoord op de client wilt starten, gebruikt u de `DRMManager.authenticate()` ActionScript- of iOS-API.

Als de client en server een aangepast verificatiemechanisme gebruiken, verkrijgt de client een verificatietoken via een ander kanaal en wordt het aangepaste verificatietoken ingesteld met behulp van het `DRMManager.setAuthenticationToken` ActionScript 3.0 API. Gebruiken `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.
