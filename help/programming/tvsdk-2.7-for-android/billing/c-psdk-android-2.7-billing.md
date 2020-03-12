---
description: Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.
seo-description: Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.
seo-title: Factureringscijfers
title: Factureringscijfers
uuid: 4a03995a-60f6-440e-9cdf-9c0b9c5f1d90
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Overzicht {#billing-metrics-overview}

Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.

Telkens wanneer de speler een streamstartgebeurtenis genereert, verzendt TVSDK regelmatig HTTP-berichten naar het factureringssysteem van Adobe. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de werkelijke waarden.

De berichten bevatten de volgende informatie:

* Inhoudstype (live, lineair of VOD)
* Inhoud-URL
* Of advertenties zijn ingeschakeld
* Of mid-roll-advertenties zijn ingeschakeld (alleen VOD)
* Of de stream door DRM is beveiligd
* De TVSDK-versie en -platform

Adobe configureert deze indeling vooraf, maar u kunt samen met uw Adobe Enablement-vertegenwoordiger de rangschikking wijzigen en samenwerken met uw Adobe Enablement-vertegenwoordiger.

Als u de statistieken wilt controleren die TVSDK naar Adobe verzendt, vraagt u de URL bij uw Adobe Enablement-vertegenwoordiger en gebruikt u een hulpprogramma voor het vastleggen van netwerken, zoals Charles, om de gegevens te bekijken.
