---
title: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
description: De Adobe Primetime DRM-server upgraden voor beveiligde streaming
copied-description: true
exl-id: 6edfba1b-46a2-4cbd-bc14-feeef1a36ed6
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# De Adobe Primetime DRM-server upgraden voor beveiligde streaming{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Als u een upgrade wilt uitvoeren van een server waarop de Primetime DRM-server voor beveiligde streaming wordt uitgevoerd, moet u de `flashaccessserver.war` bestand dat op uw toepassingsserver is geïmplementeerd met het bestand dat bij de meest recente Primetime DRM is geleverd.

Als u de nieuwe configuratieopties wilt gebruiken, moet u de server bijwerken `flashaccess-tenant.xml`. U moet ook bijwerken [!DNL jsafe.dll] of [!DNL libjsafe.so] met de versie die is opgenomen met de nieuwste Primetime DRM.
