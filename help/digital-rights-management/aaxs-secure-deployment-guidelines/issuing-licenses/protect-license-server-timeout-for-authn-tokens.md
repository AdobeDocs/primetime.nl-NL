---
title: Time-out voor verificatietokens
description: Time-out voor verificatietokens
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Time-out voor verificatietokens{#timeout-for-authentication-tokens}

Alle authentificatietokens die door de Toegang SDK van de Adobe worden geproduceerd hebben een onderbrekingsinterval om toepassingsveiligheid te beschermen. De vervaldatum voor het authentificatietoken wordt gespecificeerd gebruik Adobe Access SDK wanneer het behandelen van een authentificatieverzoek. Zodra de vervaldatum is overgegaan, is het authentificatietoken niet meer geldig en de gebruiker moet opnieuw voor authentiek verklaren met de vergunningsserver.

Meer over authentificatieverzoeken leren, zie AuthenticationHandler in *Adobe Toegang API Verwijzing*.
