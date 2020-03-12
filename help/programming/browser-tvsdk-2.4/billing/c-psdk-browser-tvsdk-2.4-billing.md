---
description: Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.
seo-description: Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.
seo-title: Factureringscijfers
title: Factureringscijfers
uuid: e09b77b3-89d3-44d6-be4e-e1612fbf89fc
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Overzicht {#billing-metrics-overview}

Om klanten die alleen willen betalen voor wat ze gebruiken in plaats van een vaste prijs, ongeacht het werkelijke gebruik, te kunnen opnemen, verzamelt Adobe gebruiksmaatstaven en gebruikt Adobe deze meetgegevens om te bepalen hoeveel ze de klanten in rekening willen brengen.

Telkens wanneer de speler een streamstartgebeurtenis genereert, verzendt Browser TVSDK regelmatig HTTP-berichten naar het factureringssysteem van Adobe. De periode, die ook wel factureerbare duur wordt genoemd, kan verschillen voor standaard VOD, pro VOD (mid-roll ads ingeschakeld) en live inhoud. De standaardduur voor elk inhoudstype is 30 minuten, maar uw contract met Adobe bepaalt de werkelijke waarden.

De berichten bevatten de volgende informatie:

* Inhoudstype (live, lineair of VOD)
* Inhoud-URL
* Of advertenties zijn ingeschakeld
* Of mid-roll-advertenties zijn ingeschakeld (alleen VOD)
* Of de stream door DRM is beveiligd
* De TVSDK-versie en -platform van de browser

Adobe configureert deze indeling vooraf, maar als u de rangschikking wilt wijzigen, werkt u samen met uw Adobe Enablement-vertegenwoordiger.

Als u de statistieken wilt controleren die Browser TVSDK naar Adobe verzendt, vraagt u de URL bij uw Adobe Enablement-vertegenwoordiger en gebruikt u een hulpprogramma voor het vastleggen van netwerken, bijvoorbeeld Charles, om de gegevens te bekijken.
