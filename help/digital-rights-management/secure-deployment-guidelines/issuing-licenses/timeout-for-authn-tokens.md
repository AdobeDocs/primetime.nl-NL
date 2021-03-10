---
description: Alle verificatietokens die door de Adobe Primetime DRM SDK worden gegenereerd, hebben een time-outinterval om de toepassingsbeveiliging te beschermen.
title: Time-out voor verificatietokens
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Time-out voor verificatietokens{#timeout-for-authentication-tokens}

Alle verificatietokens die door de Adobe Primetime DRM SDK worden gegenereerd, hebben een time-outinterval om de toepassingsbeveiliging te beschermen.

De vervaldatum voor het authentificatietoken wordt gespecificeerd gebruik Primetime DRM SDK wanneer het behandelen van een authentificatieverzoek. Nadat deze is verlopen, is het token niet meer geldig en moet de gebruiker opnieuw worden geverifieerd met de licentieserver.

Voor meer informatie over authentificatieverzoeken, zie [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).
