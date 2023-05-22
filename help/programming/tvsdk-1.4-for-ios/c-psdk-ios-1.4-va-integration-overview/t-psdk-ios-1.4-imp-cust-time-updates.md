---
description: In sommige analytische implementaties, zou de cliënttoepassing een verschillende playhead positie kunnen willen verstrekken dan de positie die door de waarde localTime van TVSDK wordt gemeld. Tijdens het afspelen van een lineaire stream kan bijvoorbeeld de afspeelkop van elk programma worden opgegeven ten opzichte van de begintijd.
title: Aangepaste tijdupdates implementeren
exl-id: 85ec4744-541f-451f-95a3-063dd1151635
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Aangepaste tijdupdates implementeren{#implement-custom-time-updates}

In sommige analytische implementaties, zou de cliënttoepassing een verschillende playhead positie kunnen willen verstrekken dan de positie die door de waarde localTime van TVSDK wordt gemeld. Tijdens het afspelen van een lineaire stream kan bijvoorbeeld de afspeelkop van elk programma worden opgegeven ten opzichte van de begintijd.

>[!TIP]
>
>Overschrijf deze methode alleen als u een andere positie voor de afspeelkop wilt opgeven dan de standaardpositie.

1. De standaardpositie van de afspeelkop overschrijven:

   ```
   vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
       NSInteger random = arc4random() % 500;  
       return CMTimeMakeWithSeconds(random, 1); 
   };
   ```

   >[!IMPORTANT]
   >
   >In dit codevoorbeeld is 500 slechts een samplewaarde. U moet een andere waarde gebruiken voor de aangepaste positie van de afspeelkop.
