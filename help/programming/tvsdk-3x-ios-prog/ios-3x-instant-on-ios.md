---
description: Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.
title: Direct aan
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Direct aan {#instant-on}

Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.

Wanneer de speler zich in de `PTMediaPlayerStatusReady` status, aanroepen `prepareToPlay` om bepaalde inhoud vooraf te laden en te verwerken voor later afspelen.

>[!TIP]
>
>Als u niet roept `prepareToPlay`, aanroepen `play` automatisch aanroepen `prepareToPlay` eerst. Het voorladen en verwerken is op dit moment voltooid.

TVSDK voert enkele of alle volgende taken uit voor `prepareToPlay`:

* Als de toets met metagegevens `kSyncCookiesWithAVAsset` Als deze optie is ingesteld, vraagt TVSDK het oorspronkelijke M3U8-bestand om cookies te synchroniseren.
* Hiermee worden DRM-metagegevenssleutels geladen.
* Hiermee maakt en bereidt u bepaalde structuren, elementen of elementen voor die nodig zijn voor het afspelen van inhoud.

>[!TIP]
>
>De `PTMediaPlayer` en `PTMediaPlayerItem` `prepareToPlay` methoden zijn gelijk. Als u geen afzonderlijke `PTMediaPlayer` -instantie voor elk element gebruiken `PTMediaPlayerItem` methode.

Met InstantOn kunt u in al deze gevallen meerdere instanties van de mediaspeler, of instanties van de lader voor items van de mediaspeler, gelijktijdig starten in de videostreams op de achtergrond en in de buffer. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt `play` op het nieuwe kanaal begint de playback eerder.
