---
description: Een lijst met toegestane entiteiten is een lijst met vertrouwde entiteiten.
seo-description: Een lijst met toegestane entiteiten is een lijst met vertrouwde entiteiten.
seo-title: Een lijst met vertrouwde inhoudspakketten bijhouden
title: Een lijst met vertrouwde inhoudspakketten bijhouden
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---


# Een toegestane lijst met vertrouwde inhoudspakketten bijhouden{#maintain-a-allowlist-of-trusted-content-packagers}

Een lijst met toegestane entiteiten is een lijst met vertrouwde entiteiten.

Voor inhoudspakketten zijn de entiteiten organisaties die door de eigenaar van de inhoud worden vertrouwd om de videobestanden te verpakken (of te coderen) en DRM-beveiligde inhoud te maken. Wanneer u Adobe Primetime DRM implementeert, moet u een lijst met vertrouwde inhoudspakketten bijhouden. U moet ook de identiteit verifiëren van de inhoudspakket in de DRM-metagegevens van een DRM-beveiligd bestand voordat u een licentie afgeeft.

Zie [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())voor informatie over de entiteit die de inhoud in een pakket heeft opgenomen.
