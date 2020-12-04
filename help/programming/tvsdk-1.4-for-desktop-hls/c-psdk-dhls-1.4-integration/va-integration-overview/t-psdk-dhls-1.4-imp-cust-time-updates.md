---
description: In bepaalde analytische implementaties wil de clienttoepassing mogelijk een andere afspeelkoppositie opgeven dan de locatie die door de lokaleTime-waarde voor TVSDK wordt gerapporteerd. Bijvoorbeeld, tijdens een LINEAR stroomplayback, kan playhead van elk programma met betrekking tot het zijn begintijd worden verstrekt.
seo-description: In bepaalde analytische implementaties wil de clienttoepassing mogelijk een andere afspeelkoppositie opgeven dan de locatie die door de lokaleTime-waarde voor TVSDK wordt gerapporteerd. Bijvoorbeeld, tijdens een LINEAR stroomplayback, kan playhead van elk programma met betrekking tot het zijn begintijd worden verstrekt.
seo-title: Aangepaste tijdupdates implementeren
title: Aangepaste tijdupdates implementeren
uuid: 2b46eca9-3815-4c44-ab5e-21678c35f410
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '181'
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

