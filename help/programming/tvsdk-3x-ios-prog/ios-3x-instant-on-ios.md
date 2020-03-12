---
description: Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.
seo-description: Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.
seo-title: Direct aan
title: Direct aan
uuid: 98a5ef79-51e4-474e-a6e8-ca449c430b5e
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Direct aan {#instant-on}

Met Instant-on worden delen van het medium op een of meer kanalen vooraf geladen. Nadat een gebruiker kanalen selecteert of schakelt, begint de inhoud eerder omdat een deel van het bufferen reeds heeft voltooid.

Wanneer de speler de `PTMediaPlayerStatusReady` status heeft, roept u `prepareToPlay` aan om bepaalde inhoud vooraf te laden en deze later af te spelen.

>[!TIP]
>
>Als u niet roept `prepareToPlay`, roept het roepen `play` automatisch eerst `prepareToPlay` . Het voorladen en verwerken is op dit moment voltooid.

TVSDK voert enkele of alle volgende taken uit voor `prepareToPlay`:

* Als de metagegevenssleutel `kSyncCookiesWithAVAsset` is ingesteld, vraagt TVSDK één keer naar het oorspronkelijke M3U8-bestand om cookies te synchroniseren.
* Hiermee worden DRM-metagegevenssleutels geladen.
* Hiermee maakt en bereidt u bepaalde structuren, elementen of elementen voor die nodig zijn voor het afspelen van inhoud.

>[!TIP]
>
>De methoden `PTMediaPlayer` en `PTMediaPlayerItem``prepareToPlay` zijn gelijk. Gebruik de `PTMediaPlayer` methode om te voorkomen dat voor elk element een aparte `PTMediaPlayerItem` instantie wordt gemaakt.

Met InstantOn kunt u in al deze gevallen meerdere instanties van de mediaspeler, of instanties van de lader voor items van de mediaspeler, gelijktijdig starten in de videostreams op de achtergrond en in de buffer. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen eerder gestart wanneer u `play` het nieuwe kanaal aanroept.