---
description: Een whitelist is een lijst met vertrouwde entiteiten.
seo-description: Een whitelist is een lijst met vertrouwde entiteiten.
seo-title: Een whitelist bijhouden van vertrouwde inhoudpakketten
title: Een whitelist bijhouden van vertrouwde inhoudpakketten
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Een whitelist bijhouden van vertrouwde inhoudpakketten{#maintain-a-whitelist-of-trusted-content-packagers}

Een whitelist is een lijst met vertrouwde entiteiten.

Voor inhoudspakketten zijn de entiteiten organisaties die door de eigenaar van de inhoud worden vertrouwd om de videobestanden te verpakken (of te coderen) en DRM-beveiligde inhoud te maken. Wanneer u Adobe Primetime DRM implementeert, moet u een whitelist van vertrouwde inhoudspakketten bijhouden. U moet ook de identiteit verifiëren van de inhoudspakket in de DRM-metagegevens van een DRM-beveiligd bestand voordat u een licentie afgeeft.

Zie [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())voor informatie over de entiteit die de inhoud in een pakket heeft opgenomen.
