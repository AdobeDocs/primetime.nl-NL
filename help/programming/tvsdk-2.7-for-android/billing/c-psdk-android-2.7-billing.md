---
description: Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek verzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.
title: Factureringscijfers
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Overzicht {#billing-metrics-overview}

Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek verzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.

Telkens wanneer de speler een streamstartgebeurtenis genereert, begint TVSDK regelmatig HTTP-berichten naar het Adobe systeem te verzenden. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de werkelijke waarden.

De berichten bevatten de volgende informatie:

* Inhoudstype (live, lineair of VOD)
* Inhoud-URL
* Of advertenties zijn ingeschakeld
* Of mid-roll-advertenties zijn ingeschakeld (alleen VOD)
* Of de stream door DRM is beveiligd
* De TVSDK-versie en -platform

Adobe vormt deze regeling vooraf, maar u kunt met uw vertegenwoordiger van Inschakelen van de Adobe werken om de regeling te veranderen, met uw vertegenwoordiger van Adobe te werken Enablement.

Om de statistieken te controleren die TVSDK naar Adobe verzendt, verkrijg URL van uw vertegenwoordiger van Inablement van de Adobe, en gebruik een netwerk vangt hulpmiddel, zoals Charles, om de gegevens te zien.
