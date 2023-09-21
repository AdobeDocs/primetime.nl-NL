---
title: Gebruikersverificatie
description: Gebruikersverificatie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Gebruikersverificatie{#user-authentication}

Een verzoek van de Toegang van de Adobe kan een authentificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek een `AuthenticationToken` door de `AuthenticationHandler`. Om tot het teken toegang te hebben en te verifiëren, gebruik `RequestMessageBase.getAuthenticationToken()`. Als u een aanvraag voor een gebruikersnaam/wachtwoord op de client wilt starten, gebruikt u de `DRMManager.authenticate()` ActionScript of iOS API.

Als de client en server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client een verificatietoken via een ander kanaal en wordt het aangepaste verificatietoken ingesteld met behulp van het `DRMManager.setAuthenticationToken` ActionScript 3.0 API. Gebruiken `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie is verantwoordelijk voor het bepalen of het token voor aangepaste verificatie geldig is.
