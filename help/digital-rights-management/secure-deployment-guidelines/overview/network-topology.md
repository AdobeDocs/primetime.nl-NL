---
title: Overzicht van netwerktopologie
description: Overzicht van netwerktopologie
copied-description: true
exl-id: a4737ea3-407a-48fd-ae3e-4df56a4c1812
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Overzicht {#network-topology-overview}

Nadat u Adobe Primetime DRM hebt geïmplementeerd, moet u de beveiliging van de Primetime DRM-productieserver behouden.

>[!NOTE]
>
>Primetime DRM stond eerder bekend als Adobe Access, en daarvoor, Flash Access.

U kunt een *reverse, proxy* om ervoor te zorgen dat verschillende sets URL&#39;s voor Primetime DRM-webtoepassingen beschikbaar zijn voor externe en interne gebruikers. *Proxy omkeren* is veiliger dan gebruikers toestaan om rechtstreeks met de toepassingsserver te verbinden waarop Primetime DRM loopt, en deze configuratie voert alle HTTP- verzoeken voor de toepassingsserver uit die Primetime DRM in werking stelt. Gebruikers hebben alleen toegang tot reverse-proxy&#39;s en kunnen alleen de URL-verbindingen proberen die door de reverse-proxy worden ondersteund.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)
