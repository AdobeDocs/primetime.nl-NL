---
title: Overzicht van netwerktopologie
description: Overzicht van netwerktopologie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---

# Overzicht van netwerktopologie {#network-topology-overview}

Nadat u met succes de Toegang van de Adobe opstelt, is het belangrijk om de veiligheid van uw milieu te handhaven. Deze sectie beschrijft de taken die noodzakelijk zijn om de veiligheid van uw de productieserver van de Toegang van de Adobe te handhaven.

Een *reverse, proxy* om ervoor te zorgen dat verschillende sets URL&#39;s voor Adobe Access-webtoepassingen beschikbaar zijn voor zowel externe als interne gebruikers. Deze configuratie is veiliger dan gebruikers toe te staan om rechtstreeks met de toepassingsserver te verbinden waarop de Toegang van de Adobe loopt. De reverse-proxy voert alle HTTP-aanvragen uit voor de toepassingsserver waarop Adobe Access wordt uitgevoerd. Gebruikers hebben alleen netwerktoegang tot de reverse-proxy en kunnen alleen de URL-verbindingen proberen die door de reverse-proxy worden ondersteund.

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)
