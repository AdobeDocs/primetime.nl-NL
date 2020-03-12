---
seo-title: Externe en lokale iOS-sleutellevering
title: Externe en lokale iOS-sleutellevering
uuid: 3c20b1d1-f842-438a-ae3a-4ec31da306ad
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Externe en lokale iOS-sleutellevering{#remote-and-local-ios-key-delivery}

Adobe Primetime ondersteunt twee opties voor het leveren van sleutels aan iOS-clients:

* Extern - Precies zoals opgegeven in de HLS-specificatie, geeft het M3U8-manifest een HTTPS-pad op dat een AES-sleutel bevat die moet worden gebruikt om de volgende gecodeerde segmenten in de stream te decoderen. Wanneer &quot;Extern&quot; is opgegeven, bereikt het clientapparaat een externe HTTPS-server om de AES-sleutel op te halen.
* Lokaal - Wanneer &quot;Lokaal&quot; is opgegeven in plaats van via internet/netwerk te reiken voor de AES-sleutel, wordt een lokale HTTPS-server ingesloten in de iOS-toepassing die alle AES-sleutelaanvragen afhandelt. De ingesloten HTTPS-server wordt automatisch ingesteld en geconfigureerd in de Primetime-toepassing. De ontwikkelaar van de toepassing heeft geen interventie nodig.

De levering van de externe sleutel wordt ingeschakeld via het beleid dat wordt gebruikt voor het verpakken van inhoud (voor het wijzigen van deze instelling moet de inhoud opnieuw worden verpakt). Wanneer levering via externe sleutel is ingeschakeld, moet een Adobe Access Key Server worden geïmplementeerd voor het afhandelen van belangrijke aanvragen van iOS-clients, maar er is geen wijziging in de workflow voor clients op andere platforms.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>De selectie voor belangrijke levering is alleen van invloed op iOS-clients. Alle andere apparaten die HLS-inhoud verbruiken, zullen altijd &quot;Lokale&quot;zeer belangrijke levering gebruiken, zelfs als &quot;Verre&quot;is gespecificeerd.

Zie *Adobe Access Key Server* gebruiken voor meer informatie.
