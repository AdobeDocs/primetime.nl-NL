---
title: Aan de slag met Adobe Primetime Ad Insertion
description: Aan de slag met Adobe Primetime Ad Insertion
translation-type: tm+mt
source-git-commit: 2a9bb089cda2b315f91b30d5cab0db9b3e372799
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Aan de slag met Adobe Primetime Ad Insertion {#ptai-get-started}

Primetime Ad Insertion coördineert de systemen die inhoud en advertenties leveren om persoonlijke, in-stream advertentiervaringen te maken en vervolgens het afspelen van advertenties voor uw adverteerders bij te houden.

Primetime-Ad Insertion communiceert met client-toepassingen voor het afspelen van video door videomanifests opnieuw te schrijven voor doelgerichte advertenties en persoonlijke ervaringen voor elke viewer. Deze manifests combineren inhoud en advertenties die van een advertentieserver worden geleverd en kunnen eventueel metagegevens bevatten met gedetailleerde instructies voor het bijhouden van advertenties. Primetime Ad Insertion ondersteunt zowel client-side als server-side en traceren van advertenties.

Nadat het systeem correct is opgezet, zou een typisch werkschema als volgt kunnen kijken:

1. De cliënttoepassing produceert [Bootstrap URL](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) met informatie over de videostroom en verzendt een verzoek van de GET naar Primetime Ad Insertion.

1. Primetime Ad Insertion reageert door inhoudsmanifest van CDN van de uitgever terug naar de cliënttoepassing te verzenden.

1. De cliënttoepassing kiest aangewezen stromen in geproduceerd manifest om te spelen en doet verzoeken aan Ad Insertion Primetime.

1. Primetime-Ad Insertion haalt de aangevraagde stream(s) op van de CDN-inhoud, parseert/leest alle actiemiddelen, roept de advertentieserver aan en vervangt en verbreekt indien nodig de gegevens.

1. Primetime-Ad Insertion normaliseert het manifest door bron-URL&#39;s opnieuw te schrijven en na te gaan of en creatieve elementen transcodering vereisen. <!-- see [Just-in-time ad transcoding](just-in-time-transcoding.md) and [packaging](just-in-time-repackaging.md).-->

1. Primetime Ad Insertion haalt de vereiste en creatieve elementen op en voegt de juiste fragmenten in de manifesten in.

1. Primetime Ad Insertion levert de uiteindelijke manifesten, inclusief advertenties, aan de clienttoepassing voor afspelen.

1. De levering en de viewability van de advertentie kunnen door of cliënt of server-kant en het volgen worden gemeten, zie [Het Plaatsen van de Controle van de Advisering](set-up-ad-tracking.md).

Primetime Ad Insertion ondersteunt de meeste clientconfiguraties voor HLS/DASH.
