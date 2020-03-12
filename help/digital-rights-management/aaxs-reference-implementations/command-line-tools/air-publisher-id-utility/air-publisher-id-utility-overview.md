---
seo-title: Overzicht van het hulpprogramma AIR Publisher ID
title: Overzicht van het hulpprogramma AIR Publisher ID
uuid: 31aecc0e-ad9b-43ad-ba58-77d2c999f4a4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht van het hulpprogramma AIR Publisher ID {#air-publisher-id-utility-overview}

Tijdens het maken van een AIR-bestand genereert ADT (AIR Developer Tool) een uitgevers-id. Dit is een unieke id voor het certificaat waarmee het AIR-bestand is gemaakt. Als u hetzelfde certificaat opnieuw gebruikt voor meerdere AIR-toepassingen, hebben deze dezelfde uitgevers-id. Het hulpprogramma AIR Publisher-id wordt gebruikt om de uitgevers-id voor een AIR-toepassing te berekenen. AIR-versies na 1.5.2 schrijven de gegenereerde uitgevers-id niet naar een bestand. Het is dus noodzakelijk dit gereedschap te gebruiken om de uitgevers-id te bepalen als u een whitelist van een AIR-toepassing gebruikt.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>De uitgevers-id, die wordt gebruikt voor whitelist-handhaving in AIR, is niet dezelfde als de uitgevers-id die is opgegeven door de uitgever van de toepassing in het [!DNL application.xml] bestand van de toepassing.

