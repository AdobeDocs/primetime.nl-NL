---
description: TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals bufferen of zoeken.
seo-description: TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals bufferen of zoeken.
seo-title: QoS-gebeurtenissen
title: QoS-gebeurtenissen
uuid: fd657cf0-c6d4-4e9a-b212-7d09d483cae9
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# QoS-gebeurtenissen{#qos-events}

TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals bufferen of zoeken.

Wanneer u een melding wilt ontvangen over alle gebeurtenissen die betrekking hebben op QoS, registreert u gebeurtenislisteners bij het `MediaPlayer` object voor de volgende gebeurtenissen:

| Gebeurtenis | Betekenis |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | Buffering is voltooid. |
| BufferEvent.[BUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | Buffering is gestart. |
| SeekEvent.[ZOEKEN_VOLTOOID](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | Zoeken is voltooid. |
| SeekEvent.[ZOEKEN_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | Zoeken begint. |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK heeft de zoekpositie gewijzigd als gevolg van het huidige reclamebeleid. |

