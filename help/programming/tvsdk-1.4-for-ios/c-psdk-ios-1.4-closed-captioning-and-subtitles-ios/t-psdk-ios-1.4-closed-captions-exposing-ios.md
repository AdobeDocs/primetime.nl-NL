---
description: Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.
title: Gesloten bijschriften beschikbaar maken
exl-id: 57168c6e-a958-4a89-b22b-0c9f1cab3a49
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Gesloten bijschriften beschikbaar maken {#expose-closed-captions}

Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.

Gesloten bijschriften toegankelijk maken:

1. In `PTMediaPlayer` object instellen `closedCaptionDisplayEnabled` eigenschap.

   Als de gebruiker Closed Captions heeft ingeschakeld, wordt de tekst in deze stap weergegeven.

   >[!NOTE]
   >
   >De clientgebruiker schakelt ondertiteling uit of uit met de Toegankelijkheidsinstellingen van iOS. Deze instellingen bieden ook opmaakopties.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` eigenschap is afgekeurd. Gebruiken `subtitlesOptions` eigenschap van `PTMediaPlayerItem`. Zie [Ondertiteling weergeven](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md) om gesloten bijschriften te gebruiken.
