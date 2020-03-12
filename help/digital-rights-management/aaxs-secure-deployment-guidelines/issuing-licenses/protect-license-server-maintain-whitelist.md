---
seo-title: Een whitelist bijhouden van vertrouwde inhoudpakketten
title: Een whitelist bijhouden van vertrouwde inhoudpakketten
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Een whitelist bijhouden van vertrouwde inhoudpakketten{#maintain-a-whitelist-of-trusted-content-packagers}

Een *whitelist* is een lijst met vertrouwde entiteiten. In het geval van inhoudspakketten zijn dit organisaties die door de eigenaar van de inhoud worden vertrouwd om de FLV/F4V-videobestanden te verpakken (of te coderen) en met DRM beveiligde inhoud te maken. Wanneer u Adobe Access implementeert, wordt u aangeraden een whitelist van vertrouwde inhoudspakketten bij te houden en de identiteit te verifiëren van de inhoudsverpakker in de DRM-metagegevens (de DRM-header) van een DRM-beveiligd bestand voordat u een licentie uitgeeft.

Zie voor meer informatie over het ophalen van informatie over de entiteit die de inhoud in een pakket heeft opgenomen `V2ContentMetaData.getPackagerInfo()` de *Adobe Access API-naslag*.
