---
seo-title: Overzicht van netwerktopologie
title: Overzicht van netwerktopologie
uuid: b8b072dc-8dc0-46ba-bb01-1e9b58af2681
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Overzicht {#network-topology-overview}

Nadat u Adobe Primetime DRM hebt geïmplementeerd, moet u de beveiliging van de Primetime DRM-productieserver behouden.

>[!NOTE]
>
>Primetime DRM werd voorheen Adobe Access genoemd en daarvoor Flash Access.

U kunt een *reverse-proxy* gebruiken om ervoor te zorgen dat verschillende sets URL&#39;s voor Primetime DRM-webtoepassingen beschikbaar zijn voor externe en interne gebruikers. *De omgekeerde volmacht* is veiliger dan het toestaan van gebruikers om rechtstreeks met de toepassingsserver te verbinden waarop Primetime DRM loopt, en deze configuratie voert alle HTTP- verzoeken voor de toepassingsserver uit die Primetime DRM in werking stelt. Gebruikers hebben alleen toegang tot reverse-proxy&#39;s en kunnen alleen de URL-verbindingen proberen die door de reverse-proxy worden ondersteund.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)