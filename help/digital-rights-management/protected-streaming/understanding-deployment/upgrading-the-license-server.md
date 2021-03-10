---
title: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
description: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# De Adobe Primetime DRM-server upgraden voor beveiligde streaming{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Als u een server wilt upgraden waarop de Primetime DRM-server voor beveiligde streaming wordt uitgevoerd, moet u het `flashaccessserver.war`-bestand dat op uw toepassingsserver is geïmplementeerd vervangen door het bestand dat is opgenomen met de nieuwste Primetime DRM.

Als u de nieuwe configuratieopties wilt gebruiken, moet u `flashaccess-tenant.xml` van uw server bijwerken. U moet [!DNL jsafe.dll] of [!DNL libjsafe.so] ook bijwerken met de versie die bij recentste Primetime DRM is inbegrepen.
