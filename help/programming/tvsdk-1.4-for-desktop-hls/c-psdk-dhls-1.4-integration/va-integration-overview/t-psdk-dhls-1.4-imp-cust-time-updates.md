---
description: In bepaalde analytische implementaties wil de clienttoepassing mogelijk een andere afspeelkoppositie opgeven dan de locatie die door de lokaleTime-waarde voor TVSDK wordt gerapporteerd. Bijvoorbeeld, tijdens een LINEAR stroomplayback, kan playhead van elk programma met betrekking tot het zijn begintijd worden verstrekt.
title: Aangepaste tijdupdates implementeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

