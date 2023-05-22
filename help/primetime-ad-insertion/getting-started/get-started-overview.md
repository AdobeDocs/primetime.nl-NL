---
title: Aan de slag met Adobe Primetime Ad Insertion
description: Aan de slag met Adobe Primetime Ad Insertion
exl-id: 629ea2a5-1b50-4451-a478-95d02f192145
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Aan de slag met Adobe Primetime Ad Insertion {#ptai-get-started}

Primetime Ad Insertion coördineert de systemen die inhoud en advertenties leveren om persoonlijke, in-stream advertentiervaringen te maken en vervolgens het afspelen van advertenties voor uw adverteerders bij te houden.

Primetime Ad Insertion communiceert met video-levering cliënttoepassingen door videomanifests te herschrijven om gerichte advertenties en gepersonaliseerde ervaringen voor elke kijker te verstrekken. Deze manifesten combineren inhoud en advertenties die van een advertentieserver worden geleverd en kunnen naar keuze meta-gegevens omvatten die gedetailleerde ad-volgende instructies bevatten. Primetime Ad Insertion ondersteunt zowel client-side als server-side en traceren van advertenties.

Nadat het systeem correct is opgezet, zou een typisch werkschema als volgt kunnen kijken:

1. De clienttoepassing genereert een [Bootstrap URL](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) met informatie over de videostream en verzendt een verzoek van GET naar Primetime Ad Insertion.  Primetime Ad Insertion ondersteunt HLS en DASH met een groot aantal verschillende indelingen voor advertenties.

1. Primetime Ad Insertion reageert door inhoudsmanifest van CDN van de uitgever terug naar de cliënttoepassing te verzenden.

1. De cliënttoepassing kiest aangewezen stromen in geproduceerd manifest om te spelen en doet verzoeken aan Ad Insertion Primetime.

1. Primetime-Ad Insertion haalt de aangevraagde stream(s) op van de CDN-inhoud, parseert/leest alle actiemiddelen, roept de advertentieserver aan en vervangt en verbreekt indien nodig de gegevens.

1. Primetime-Ad Insertion normaliseert het manifest door bron-URL&#39;s opnieuw te schrijven en na te gaan of ad-creatieve functies transcoderen vereisen, raadpleegt u [Just-in-Time en Transcoding](/help/primetime-ad-insertion/just-in-time-transcoding/jit-transcoding-overview.md).

1. Primetime Ad Insertion haalt de vereiste en creatieve elementen op en voegt de juiste fragmenten in de manifesten in.

1. Primetime Ad Insertion levert de uiteindelijke manifesten, inclusief advertenties, aan de clienttoepassing voor afspelen.

1. De levering en de viewability van de advertentie kunnen door of cliënt of server worden gemeten en volgen, zie [Advertentie bijhouden instellen](/help/primetime-ad-insertion/getting-started/set-up-ad-tracking.md).

Primetime Ad Insertion ondersteunt de meeste HLS/DASH-client- en spelerconfiguraties. Voor meer informatie over specifieke ondersteunde advertentievormen raadpleegt u [Ondersteunde actiefindelingen](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md).
