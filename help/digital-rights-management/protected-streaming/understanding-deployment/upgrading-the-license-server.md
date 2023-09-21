---
title: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
description: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# De Adobe Primetime DRM-server upgraden voor beveiligde streaming{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Als u een upgrade wilt uitvoeren van een server waarop de Primetime DRM-server voor beveiligde streaming wordt uitgevoerd, moet u de `flashaccessserver.war` bestand dat op uw toepassingsserver is geïmplementeerd met het bestand dat bij de meest recente Primetime DRM is geleverd.

Als u de nieuwe configuratieopties wilt gebruiken, moet u de server bijwerken `flashaccess-tenant.xml`. U moet ook bijwerken [!DNL jsafe.dll] of [!DNL libjsafe.so] met de versie die is opgenomen met de nieuwste Primetime DRM.
