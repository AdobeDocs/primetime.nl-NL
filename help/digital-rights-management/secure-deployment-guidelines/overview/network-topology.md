---
title: Overzicht van netwerktopologie
description: Overzicht van netwerktopologie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Overzicht {#network-topology-overview}

Nadat u Adobe Primetime DRM hebt geïmplementeerd, moet u de beveiliging van de Primetime DRM-productieserver behouden.

>[!NOTE]
>
>Primetime DRM was eerder gekend als Toegang van de Adobe, en voordien, Flash Access.

U kunt een *reverse, proxy* om ervoor te zorgen dat verschillende sets URL&#39;s voor Primetime DRM-webtoepassingen beschikbaar zijn voor externe en interne gebruikers. *Proxy omkeren* is veiliger dan gebruikers toestaan om rechtstreeks met de toepassingsserver te verbinden waarop Primetime DRM loopt, en deze configuratie voert alle HTTP- verzoeken voor de toepassingsserver uit die Primetime DRM in werking stelt. Gebruikers hebben alleen toegang tot reverse-proxy&#39;s en kunnen alleen de URL-verbindingen proberen die door de reverse-proxy worden ondersteund.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)
