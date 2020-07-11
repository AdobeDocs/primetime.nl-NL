---
description: Een lijst van gewenste personen is een lijst met vertrouwde entiteiten.
seo-description: Een lijst van gewenste personen is een lijst met vertrouwde entiteiten.
seo-title: Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden
title: Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden {#maintain-a-allowlist-of-trusted-content-packagers}

Een lijst van gewenste personen is een lijst met vertrouwde entiteiten.

Voor inhoudspakketten zijn de entiteiten organisaties die door de eigenaar van de inhoud worden vertrouwd om de videobestanden te verpakken (of te coderen) en DRM-beveiligde inhoud te maken. Wanneer u Adobe Primetime DRM implementeert, moet u een lijst van gewenste personen van vertrouwde inhoudspakketten onderhouden. U moet ook de identiteit verifiëren van de inhoudspakket in de DRM-metagegevens van een DRM-beveiligd bestand voordat u een licentie afgeeft.

Zie [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())voor informatie over de entiteit die de inhoud in een pakket heeft opgenomen.
