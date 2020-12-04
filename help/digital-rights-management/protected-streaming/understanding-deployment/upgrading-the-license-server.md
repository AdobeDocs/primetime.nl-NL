---
seo-title: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
title: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
uuid: 5c507ae3-d1d9-40ad-ba97-501ec92b45dc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# De Adobe Primetime DRM-server upgraden voor beveiligde streaming{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Als u een server wilt upgraden waarop de Primetime DRM-server voor beveiligde streaming wordt uitgevoerd, moet u het `flashaccessserver.war`-bestand dat op uw toepassingsserver is geïmplementeerd vervangen door het bestand dat is opgenomen met de nieuwste Primetime DRM.

Als u de nieuwe configuratieopties wilt gebruiken, moet u `flashaccess-tenant.xml` van uw server bijwerken. U moet [!DNL jsafe.dll] of [!DNL libjsafe.so] ook bijwerken met de versie die bij recentste Primetime DRM is inbegrepen.
