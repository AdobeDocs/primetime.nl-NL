---
title: Overzicht van netwerktopologie
description: Overzicht van netwerktopologie
copied-description: true
exl-id: ca5e8701-f8a3-4125-bb60-bfb9efd5c8f3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---

# Overzicht van netwerktopologie {#network-topology-overview}

Nadat u met succes de Toegang van Adobe opstelt, is het belangrijk om de veiligheid van uw milieu te handhaven. Deze sectie beschrijft de taken die noodzakelijk zijn om de veiligheid van uw de productieserver van de Toegang van de Adobe te handhaven.

Een *reverse, proxy* om ervoor te zorgen dat verschillende sets URL&#39;s voor Adobe Access-webtoepassingen beschikbaar zijn voor zowel externe als interne gebruikers. Deze configuratie is veiliger dan gebruikers toe te staan om rechtstreeks met de toepassingsserver te verbinden waarop Adobe Access loopt. De reverse-proxy voert alle HTTP-aanvragen uit voor de toepassingsserver waarop Adobe Access wordt uitgevoerd. Gebruikers hebben alleen netwerktoegang tot de reverse-proxy en kunnen alleen de URL-verbindingen proberen die door de reverse-proxy worden ondersteund.

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)
