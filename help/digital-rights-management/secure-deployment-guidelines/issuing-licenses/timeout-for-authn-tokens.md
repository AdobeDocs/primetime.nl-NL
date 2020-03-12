---
description: Alle verificatietokens die door de Adobe Primetime DRM SDK worden gegenereerd, hebben een time-outinterval om de toepassingsbeveiliging te beschermen.
seo-description: Alle verificatietokens die door de Adobe Primetime DRM SDK worden gegenereerd, hebben een time-outinterval om de toepassingsbeveiliging te beschermen.
seo-title: Time-out voor verificatietokens
title: Time-out voor verificatietokens
uuid: 2c2b0dad-0979-4d49-b109-2700ceb4d722
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# Time-out voor verificatietokens{#timeout-for-authentication-tokens}

Alle verificatietokens die door de Adobe Primetime DRM SDK worden gegenereerd, hebben een time-outinterval om de toepassingsbeveiliging te beschermen.

De vervaldatum voor het authentificatietoken wordt gespecificeerd gebruik Primetime DRM SDK wanneer het behandelen van een authentificatieverzoek. Nadat deze is verlopen, is het token niet meer geldig en moet de gebruiker opnieuw worden geverifieerd met de licentieserver.

Meer over authentificatieverzoeken leren, zie [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).
