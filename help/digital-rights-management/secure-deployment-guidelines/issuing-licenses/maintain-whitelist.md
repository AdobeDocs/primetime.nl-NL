---
description: Een lijst van gewenste personen is een lijst met vertrouwde entiteiten.
title: Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden {#maintain-a-allowlist-of-trusted-content-packagers}

Een lijst van gewenste personen is een lijst met vertrouwde entiteiten.

Voor inhoudspakketten zijn de entiteiten organisaties die door de eigenaar van de inhoud worden vertrouwd om de videobestanden te verpakken (of te coderen) en DRM-beveiligde inhoud te maken. Wanneer u Adobe Primetime DRM implementeert, moet u een lijst van gewenste personen vertrouwde inhoudspakketten onderhouden. U moet ook de identiteit verifiëren van de inhoudspakket in de DRM-metagegevens van een DRM-beveiligd bestand voordat u een licentie afgeeft.

Ga voor meer informatie over de entiteit die de inhoud in een pakket heeft geplaatst naar [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).
