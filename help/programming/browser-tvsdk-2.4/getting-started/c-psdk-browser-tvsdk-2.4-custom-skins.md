---
description: Als u de aangepaste skins wilt gebruiken, moet u de aanpassing schrijven, vergelijkbaar met default-video-controls.css en naar deze nieuwe aanpassing in de speler verwijzen.
title: Aangepaste skins
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Aangepaste skins{#custom-skins}

Als u de aangepaste skins wilt gebruiken, moet u de aanpassing schrijven, vergelijkbaar met default-video-controls.css en naar deze nieuwe aanpassing in de speler verwijzen.

U kunt bijvoorbeeld een van de volgende opties gebruiken:

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

U kunt de volgende typen wijzigingen aanbrengen:

* Voorgrondkleur van knoppen en tekst

   Alle besturingselementen met een voorgrond gebruiken de klasse `vid-skin-fgcolor`. Als u de voorgrond van alle besturingselementen wilt wijzigen, doorloopt u alle elementen met de klasse `vid-skin-fgcolor` en geeft u de gewenste kleur op.
* Achtergrondkleur van knoppen en tekst

   Alle controles die een voorgrond hebben gebruiken de `vid-skin-bgcolor` klasse. Als u de voorgrond van alle besturingselementen wilt wijzigen, doorloopt u alle elementen met de klasse `vid-skin-bgcolor` en geeft u de gewenste kleur op.
* Vorm van de afspeelkop

   De afspeelkop kan vierkant of rond zijn. Als u de afspeelkop wilt wijzigen, voegt u de klasse `square` of `round` toe aan het element `playhead`.
* Stijl van de bufferspinners

   De referentiespeler biedt de volgende stijlen van spinners die kunnen worden weergegeven als inhoud voor buffers van de speler:

   * Overlay-tekst ( `overlay-text`)
   * Rechthoekige spinner ( `spinner`)
   * Signaal ( `signal`)
   * Verticale balken ( `vertical`)

      >[!TIP]
      >
      >Als u een van de bufferspinners wilt gebruiken, moet u de klasse in het buffering-overlay-element toevoegen. Als u bijvoorbeeld `overlay-text` wilt gebruiken, voegt u de volgende regels toe aan het bestand `BufferOverlay.js`:
      >
      >
      ```js
      >var overlay = document.getElementById("buffering-overlay"); 
      >overlay.classList.add ("spinner");
      >```

