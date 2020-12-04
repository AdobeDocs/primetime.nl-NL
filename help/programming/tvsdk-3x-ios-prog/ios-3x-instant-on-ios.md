---
description: Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.
seo-description: Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.
seo-title: Direct aan
title: Direct aan
uuid: 98a5ef79-51e4-474e-a6e8-ca449c430b5e
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Instant-on {#instant-on}

Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.

Wanneer uw speler in de `PTMediaPlayerStatusReady` status is, vraag `prepareToPlay` om sommige inhoud voor recentere playback vooraf te laden en te verwerken.

>[!TIP]
>
>Als u `prepareToPlay` niet roept, roept het roepen `play` automatisch `prepareToPlay` eerst. Het voorladen en verwerken is op dit moment voltooid.

TVSDK voert enkele of alle volgende taken uit voor `prepareToPlay`:

* Als de metagegevenssleutel `kSyncCookiesWithAVAsset` is ingesteld, vraagt TVSDK één keer naar het oorspronkelijke M3U8-bestand om cookies te synchroniseren.
* Hiermee worden DRM-metagegevenssleutels geladen.
* Hiermee maakt en bereidt u bepaalde structuren, elementen of elementen voor die nodig zijn voor het afspelen van inhoud.

>[!TIP]
>
>De methoden `PTMediaPlayer` en `PTMediaPlayerItem` `prepareToPlay` zijn gelijk. Als u wilt voorkomen dat voor elk element een afzonderlijke `PTMediaPlayer`-instantie wordt gemaakt, gebruikt u de methode `PTMediaPlayerItem`.

Met InstantOn kunt u in al deze gevallen meerdere instanties van de mediaspeler, of instanties van de lader voor items van de mediaspeler, gelijktijdig starten in de videostreams op de achtergrond en in de buffer. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen eerder gestart wanneer `play` op het nieuwe kanaal wordt aangeroepen.