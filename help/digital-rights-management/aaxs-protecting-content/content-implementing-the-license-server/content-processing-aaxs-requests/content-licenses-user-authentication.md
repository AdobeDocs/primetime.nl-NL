---
title: Gebruikersverificatie
description: Gebruikersverificatie
copied-description: true
exl-id: a0dd7d81-2249-4845-94da-53b755d6cd7c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Gebruikersverificatie{#user-authentication}

Een verzoek van de Toegang van Adobe kan een authentificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek een `AuthenticationToken` door de `AuthenticationHandler`. Om tot het teken toegang te hebben en te verifiëren, gebruik `RequestMessageBase.getAuthenticationToken()`. Als u een aanvraag voor een gebruikersnaam/wachtwoord op de client wilt starten, gebruikt u de `DRMManager.authenticate()` ActionScript- of iOS-API.

Als de client en server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client een verificatietoken via een ander kanaal en wordt het aangepaste verificatietoken ingesteld met behulp van het `DRMManager.setAuthenticationToken` ActionScript 3.0 API. Gebruiken `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.
