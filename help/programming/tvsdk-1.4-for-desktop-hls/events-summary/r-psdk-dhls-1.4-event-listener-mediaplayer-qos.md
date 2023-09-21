---
description: TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals bufferen of zoeken.
title: QoS-gebeurtenissen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# QoS-gebeurtenissen{#qos-events}

TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals bufferen of zoeken.

Om op de hoogte te worden gebracht van alle gebeurtenissen die betrekking hebben op QoS, registreert u gebeurtenislisteners bij de `MediaPlayer` object voor de volgende gebeurtenissen:

| Gebeurtenis | Betekenis |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | Buffering is voltooid. |
| BufferEvent.[BUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | Buffering is gestart. |
| SeekEvent.[ZOEKEN_VOLTOOID](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | Zoeken is voltooid. |
| SeekEvent.[ZOEKEN_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | Zoeken begint. |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK heeft de zoekpositie gewijzigd als gevolg van het huidige reclamebeleid. |
