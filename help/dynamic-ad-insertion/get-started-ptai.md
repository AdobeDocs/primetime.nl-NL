---
title: Aan de slag met Adobe Primetime Ad Insertion
description: Aan de slag met Adobe Primetime Ad Insertion
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Aan de slag met Adobe Primetime Ad Insertion {#ptai-get-started}

Primetime Ad Insertion coördineert de systemen die inhoud en advertenties leveren om persoonlijke, in-stream advertentiervaringen te maken en vervolgens het afspelen van advertenties voor uw adverteerders bij te houden.

Primetime-Ad Insertion communiceert met client-toepassingen voor het afspelen van video door videomanifests opnieuw te schrijven voor doelgerichte advertenties en persoonlijke ervaringen voor elke viewer. Deze manifests combineren inhoud en advertenties die van een advertentieserver worden geleverd en kunnen eventueel metagegevens bevatten met gedetailleerde instructies voor het bijhouden van advertenties. Primetime Ad Insertion ondersteunt zowel client-side als server-side en traceren van advertenties.

Nadat het systeem correct is opgezet, zou een typisch werkschema als volgt kunnen kijken:

1. De clienttoepassing genereert een [Bootstrap-URL](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md) met informatie over de videostream en verzendt een verzoek van de GET naar Primetime Ad Insertion.

1. Primetime Ad Insertion reageert door inhoudsmanifest van CDN van de uitgever terug naar de cliënttoepassing te verzenden.

1. De cliënttoepassing kiest aangewezen stromen in geproduceerd manifest om te spelen en doet verzoeken aan Ad Insertion Primetime.

1. Primetime-Ad Insertion haalt de aangevraagde stream(s) op van de CDN-inhoud, parseert/leest alle actiemiddelen, roept de advertentieserver aan en vervangt en verbreekt indien nodig de gegevens.

1. Primetime Ad Insertion normaliseert manifest door middel van herschrijven bron URLs en het ontdekken of ad creatieve transcodering vereist, zie [just-in-time en transcodering](just-in-time-transcoding.md) en [verpakking](just-in-time-repackaging.md).

1. Primetime Ad Insertion haalt de vereiste en creatieve elementen op en voegt de juiste fragmenten in de manifesten in.

1. Primetime Ad Insertion levert de uiteindelijke manifesten, inclusief advertenties, aan de clienttoepassing voor afspelen.

1. De levering en de viewability van de advertentie kunnen door of cliënt of server-kant worden gemeten en volgen, zie [Opstelling en het Volgen](set-up-ad-tracking.md)van de Aanpassing.

Primetime Ad Insertion ondersteunt de meeste clientconfiguraties voor HLS/DASH.
