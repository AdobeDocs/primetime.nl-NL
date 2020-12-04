---
description: U kunt de indeling instellen voor tekst met een gesloten bijschrift, zoals lettertype, grootte, kleur, rand en dekking.
seo-description: U kunt de indeling instellen voor tekst met een gesloten bijschrift, zoals lettertype, grootte, kleur, rand en dekking.
seo-title: Stijlen voor een gesloten bijschrift instellen
title: Stijlen voor een gesloten bijschrift instellen
uuid: 906ed22c-e673-4211-a14b-d95d176aad21
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Stijlen voor een gesloten bijschrift instellen{#set-closed-caption-styles}

U kunt de indeling instellen voor tekst met een gesloten bijschrift, zoals lettertype, grootte, kleur, rand en dekking.

1. Wacht tot de status `MediaPlayer` ten minste de status PREPARED heeft.

   Voor meer informatie over de staten, zie [Wacht op een geldige staat](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md).
1. Maak een `TextFormat`-instantie.

   U kunt nu alle opmaakparameters voor een gesloten bijschrift opgeven of deze later instellen.

   ```js
   new TextFormat( 
       font,   
       fontColor,  
       edgeColor,   
       fontEdge,  
       backgroundColor,   
       fillColor,  
       size,   
       fontOpacity,   
       backgroundOpacity,  
       fillOpacity, 
       bottomInset 
       safeArea) → {AdobePSDK.TextFormat}
   ```

1. (Optioneel) U kunt de huidige instellingen voor de stijl van een gesloten bijschrift ophalen met `MediaPlayer.ccStyle`.

   De terugkeerwaarde is een geval van de `TextFormat` interface.

   Als er eerder geen stijl is ingesteld, wordt een object TextFormat met standaardwaarden voor elk kenmerk geretourneerd:

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. Als u de stijlinstellingen wilt wijzigen, gebruikt u `MediaPlayer.ccStyle` en geeft u een instantie van de interface `TextFormat` door.

   U kunt deze methode ook gebruiken als de huidige mediastream geen ondertitels heeft.

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >Het instellen van de stijl voor een gesloten bijschrift is asynchroon, dus het kan enkele seconden duren voordat de wijzigingen op het scherm worden weergegeven.

