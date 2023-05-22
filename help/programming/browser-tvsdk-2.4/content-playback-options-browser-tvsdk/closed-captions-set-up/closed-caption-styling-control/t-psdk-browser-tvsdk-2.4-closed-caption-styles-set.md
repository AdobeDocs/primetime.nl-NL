---
description: U kunt de indeling instellen voor tekst met een gesloten bijschrift, zoals lettertype, grootte, kleur, rand en dekking.
title: Stijlen voor een gesloten bijschrift instellen
exl-id: 7ece68ce-0dc5-4899-9834-39940bbd0332
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Stijlen voor een gesloten bijschrift instellen{#set-closed-caption-styles}

U kunt de indeling instellen voor tekst met een gesloten bijschrift, zoals lettertype, grootte, kleur, rand en dekking.

1. Wacht op de `MediaPlayer` ten minste in de staat PREPARED.

   Voor meer informatie over de staten raadpleegt u [Wacht op een geldige status](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md).
1. Een `TextFormat` -instantie.

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

1. (Optioneel) U kunt de huidige stijlinstellingen voor een gesloten bijschrift ophalen met `MediaPlayer.ccStyle`.

   De geretourneerde waarde is een instantie van de `TextFormat` interface.

   Als er eerder geen stijl is ingesteld, wordt een object TextFormat met standaardwaarden voor elk kenmerk geretourneerd:

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. Als u de stijlinstellingen wilt wijzigen, gebruikt u `MediaPlayer.ccStyle`, waarbij een instantie van de `TextFormat` interface.

   U kunt deze methode ook gebruiken als de huidige mediastream geen ondertitels heeft.

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >Het instellen van de stijl voor een gesloten bijschrift is asynchroon, dus het kan enkele seconden duren voordat de wijzigingen op het scherm worden weergegeven.
