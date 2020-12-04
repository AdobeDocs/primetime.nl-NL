---
seo-title: Overzicht van netwerktopologie
title: Overzicht van netwerktopologie
uuid: b8b072dc-8dc0-46ba-bb01-1e9b58af2681
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
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