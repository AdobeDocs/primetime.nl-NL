---
description: In sommige analytische implementaties, zou de cliënttoepassing een verschillende playhead positie kunnen willen verstrekken dan de positie die door de lokaleTime waarde van TVSDK wordt gemeld. Tijdens het afspelen van een lineaire stream kan bijvoorbeeld de afspeelkop van elk programma worden opgegeven ten opzichte van de begintijd.
title: Aangepaste tijdupdates implementeren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Aangepaste tijdupdates implementeren {#implement-custom-time-updates}

In sommige analytische implementaties, zou de cliënttoepassing een verschillende playhead positie kunnen willen verstrekken dan de positie die door de lokaleTime waarde van TVSDK wordt gemeld. Tijdens het afspelen van een lineaire stream kan bijvoorbeeld de afspeelkop van elk programma worden opgegeven ten opzichte van de begintijd.

>[!TIP]
>
>Overschrijf deze methode alleen als u een andere positie voor de afspeelkop dan de standaardpositie wilt opgeven.

De standaardpositie van de afspeelkop overschrijven:

```java
vaMetadata.setCurrentTimeUpdateBlock(new VideoAnalyticsMetadata.CurrentTimeUpdateBlock() { 
    @Override 
    public long call() { 
        long range = 500L; 
        Random r = new Random() 
        return (long)(r.nextDouble()*range); 
    } 
});
```

>[!IMPORTANT]
>
>De waarden in dit codefragment zijn alleen voorbeelden. U moet verschillende waarden gebruiken voor de aangepaste positie van de afspeelkop.