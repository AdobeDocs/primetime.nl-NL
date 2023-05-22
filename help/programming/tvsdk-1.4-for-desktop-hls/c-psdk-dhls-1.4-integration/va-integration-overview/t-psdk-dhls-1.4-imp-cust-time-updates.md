---
description: In bepaalde analytische implementaties wil de clienttoepassing mogelijk een andere afspeelkoppositie opgeven dan de locatie die door de lokaleTime-waarde voor TVSDK wordt gerapporteerd. Bijvoorbeeld, tijdens een LINEAR stroomplayback, kan playhead van elk programma met betrekking tot het zijn begintijd worden verstrekt.
title: Aangepaste tijdupdates implementeren
exl-id: be0f2684-6a17-4d99-8875-7f404ce8a656
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Aangepaste tijdupdates implementeren{#implement-custom-time-updates}

In bepaalde analytische implementaties wil de clienttoepassing mogelijk een andere afspeelkoppositie opgeven dan de locatie die door de lokaleTime-waarde voor TVSDK wordt gerapporteerd. Bijvoorbeeld, tijdens een LINEAR stroomplayback, kan playhead van elk programma met betrekking tot het zijn begintijd worden verstrekt.

>[!TIP]
>
>Overschrijf deze methode alleen als u een andere positie voor de afspeelkop wilt opgeven dan de standaardpositie.

1. De standaardpositie van de afspeelkop overschrijven:

   ```
   vaMetadata.currentTimeUpdateBlock = function():Number { 
      if (currentTime == 0) { 
          currentTime = getTimer(); 
      } 
      return ((getTimer() - currentTime) / 1000 + 1000); 
   }
   ```

   >[!IMPORTANT]
   >
   >De waarden in dit codefragment zijn alleen voorbeelden. U moet verschillende waarden gebruiken voor de aangepaste positie van de afspeelkop.
