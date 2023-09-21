---
description: Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek inzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.
title: Factureringscijfers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Factureringscijfers {#billing-metrics}

Om klanten aan te passen die slechts voor wat willen betalen zij, eerder dan een vast tarief ongeacht werkelijk gebruik, Adobe gebruiksmetriek inzamelen en deze metriek gebruiken om te bepalen hoeveel om de klanten in rekening te brengen.

Telkens wanneer de speler een streamstartgebeurtenis genereert, begint TVSDK regelmatig HTTP-berichten te verzenden naar het factureringssysteem van de Adobe. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de daadwerkelijke waarden.

De berichten bevatten de volgende informatie:

* Inhoudstype (live, lineair of VOD)
* Inhoud-URL
* Of advertenties zijn ingeschakeld
* Of mid-roll-advertenties zijn ingeschakeld (alleen VOD)
* Of de stream door DRM is beveiligd
* De TVSDK-versie en -platform

Adobe vormt vooraf deze regeling, maar u kunt met uw vertegenwoordiger van de Adobe werken Enablement om de regeling te veranderen, met uw vertegenwoordiger van de Adobe werken Enablement.

Om de statistieken te controleren die TVSDK naar Adobe verzendt, verkrijg URL van uw vertegenwoordiger van Inschakelen van de Adobe, en gebruik een hulpmiddel van de netwerkvangst, zoals Charles, om de gegevens te zien.
