---
seo-title: Een toegestane lijst met vertrouwde inhoudspakketten bijhouden
title: Een toegestane lijst met vertrouwde inhoudspakketten bijhouden
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Een toegestane lijst met vertrouwde inhoudspakketten bijhouden{#maintain-a-allowlist-of-trusted-content-packagers}

Een *allowlist* is een lijst met vertrouwde entiteiten. In het geval van inhoudspakketten zijn dit organisaties die door de eigenaar van de inhoud worden vertrouwd om de FLV/F4V-videobestanden te verpakken (of te coderen) en met DRM beveiligde inhoud te maken. Als u Adobe Access implementeert, wordt u aangeraden een lijst met vertrouwde inhoudspakketten bij te houden en de identiteit te verifiëren van de inhoudsverpakker in de DRM-metagegevens (de DRM-header) van een DRM-beveiligd bestand voordat u een licentie uitgeeft.

Zie voor meer informatie over het ophalen van informatie over de entiteit die de inhoud in een pakket heeft opgenomen `V2ContentMetaData.getPackagerInfo()` de *Adobe Access API-naslag*.
