---
title: Externe en lokale iOS Key Delivery
description: Externe en lokale iOS Key Delivery
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Externe en lokale iOS Key Delivery{#remote-and-local-ios-key-delivery}

Adobe Primetime ondersteunt twee opties voor belangrijke levering aan iOS-clients:

* Extern - Precies zoals opgegeven in de HLS-specificatie, geeft het M3U8-manifest een HTTPS-pad op dat een AES-sleutel bevat die moet worden gebruikt om de volgende gecodeerde segmenten in de stream te decoderen. Wanneer &quot;Extern&quot; is opgegeven, bereikt het clientapparaat een externe HTTPS-server om de AES-sleutel op te halen.
* Lokaal - Wanneer &quot;Lokaal&quot; is opgegeven in plaats van via internet/netwerk te bereiken voor de AES-sleutel, wordt een lokale HTTPS-server ingesloten in de iOS-toepassing die alle AES-sleutelverzoeken zal verwerken. De ingesloten HTTPS-server wordt automatisch ingesteld en geconfigureerd in de Primetime-toepassing. De ontwikkelaar van de toepassing heeft geen tussenkomst nodig.

De levering van de verre sleutel wordt toegelaten door het beleid dat wordt gebruikt om inhoud te verpakken (het veranderen van dit het plaatsen vereist herverpakken van inhoud), wanneer de verre zeer belangrijke levering wordt toegelaten, moet een Zeer belangrijke Server van de Toegang van de Adobe worden opgesteld om zeer belangrijke verzoeken van de cliënten van iOS te behandelen, maar er is geen verandering in het werkschema voor cliënten op andere platforms.

>[!NOTE]
>
>De selectie voor belangrijke levering is alleen van invloed op iOS-clients. Alle andere apparaten die HLS-inhoud verbruiken, zullen altijd &quot;Lokale&quot;zeer belangrijke levering gebruiken, zelfs als &quot;Verre&quot;is gespecificeerd.

Zie voor meer informatie *De sleutelserver voor toegang tot de Adobe gebruiken*.
