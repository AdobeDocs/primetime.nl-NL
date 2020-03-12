---
seo-title: Overzicht van netwerktopologie
title: Overzicht van netwerktopologie
uuid: 1558b7fa-dc0d-477c-8f1c-9c6f3718e1b0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht van netwerktopologie {#network-topology-overview}

Nadat u Adobe Access hebt geïmplementeerd, is het belangrijk dat u de beveiliging van uw omgeving behoudt. In deze sectie worden de taken beschreven die nodig zijn om de beveiliging van uw Adobe Access-productieserver te behouden.

Gebruik een *reverse-proxy* om ervoor te zorgen dat verschillende sets URL&#39;s voor Adobe Access-webtoepassingen beschikbaar zijn voor zowel externe als interne gebruikers. Deze configuratie is veiliger dan gebruikers rechtstreeks verbinding kunnen maken met de toepassingsserver waarop Adobe Access wordt uitgevoerd. De reverse-proxy voert alle HTTP-aanvragen uit voor de toepassingsserver waarop Adobe Access wordt uitgevoerd. Gebruikers hebben alleen netwerktoegang tot de reverse-proxy en kunnen alleen de URL-verbindingen proberen die door de reverse-proxy worden ondersteund.

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)

