---
title: Overzicht van netwerktopologie
description: Overzicht van netwerktopologie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Overzicht {#network-topology-overview}

Nadat u Adobe Primetime DRM hebt geïmplementeerd, moet u de beveiliging van de Primetime DRM-productieserver behouden.

>[!NOTE]
>
>Primetime DRM stond eerder bekend als Adobe Access, en daarvoor, Flash Access.

U kunt een *reverse-proxy* gebruiken om ervoor te zorgen dat verschillende sets URL&#39;s voor Primetime DRM-webtoepassingen beschikbaar zijn voor externe en interne gebruikers. *Omgekeerde* proxy is veiliger dan gebruikers toestaan om rechtstreeks verbinding te maken met de toepassingsserver waarop Primetime DRM wordt uitgevoerd, en deze configuratie voert alle HTTP-aanvragen uit voor de toepassingsserver waarop Primetime DRM wordt uitgevoerd. Gebruikers hebben alleen toegang tot reverse-proxy&#39;s en kunnen alleen de URL-verbindingen proberen die door de reverse-proxy worden ondersteund.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)