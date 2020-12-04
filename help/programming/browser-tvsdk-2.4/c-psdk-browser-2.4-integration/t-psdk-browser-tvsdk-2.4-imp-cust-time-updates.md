---
description: In sommige analytische implementaties, zou de cliënttoepassing een verschillende playhead positie kunnen willen verstrekken dan de positie die door Browser TVSDK localTime waarde wordt gemeld.
seo-description: In sommige analytische implementaties, zou de cliënttoepassing een verschillende playhead positie kunnen willen verstrekken dan de positie die door Browser TVSDK localTime waarde wordt gemeld.
seo-title: Aangepaste tijdupdates implementeren
title: Aangepaste tijdupdates implementeren
uuid: 26a0592c-a47b-4d65-b984-5e51533dcddc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# Aangepaste tijdupdates implementeren{#implement-custom-time-updates}

In sommige analytische implementaties, zou de cliënttoepassing een verschillende playhead positie kunnen willen verstrekken dan de positie die door Browser TVSDK localTime waarde wordt gemeld.

Tijdens het afspelen van een lineaire stream kan bijvoorbeeld de afspeelkop van elk programma worden opgegeven ten opzichte van de begintijd.

>[!TIP]
>
>Overschrijf deze methode alleen als u een andere positie voor de afspeelkop dan de standaardpositie wilt opgeven.

De standaardpositie van de afspeelkop overschrijven:

```js
vaMetadata.currentTimeUpdateBlock = function() { 
       return playerPositionInSeconds; 
}; 
```

>[!IMPORTANT]
>
>De waarden in dit codefragment zijn alleen voorbeelden. U moet verschillende waarden gebruiken voor de aangepaste positie van de afspeelkop.

