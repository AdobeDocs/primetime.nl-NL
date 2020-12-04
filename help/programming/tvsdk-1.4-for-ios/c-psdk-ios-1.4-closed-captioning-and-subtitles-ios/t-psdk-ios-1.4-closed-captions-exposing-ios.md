---
description: Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.
seo-description: Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.
seo-title: Gesloten bijschriften beschikbaar maken
title: Gesloten bijschriften beschikbaar maken
uuid: 209b34ca-f14e-499e-af5f-2d8c7b359ef8
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Gesloten bijschriften beschikbaar maken {#expose-closed-captions}

Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.

Gesloten bijschriften toegankelijk maken:

1. Stel in `PTMediaPlayer`-object de eigenschap `closedCaptionDisplayEnabled` in.

   Als de gebruiker Closed Captions heeft ingeschakeld, wordt de tekst in deze stap weergegeven.

   >[!NOTE]
   >
   >De gebruiker van de client schakelt ondertiteling uit of uit met behulp van de iOS-toegankelijkheidsinstellingen. Deze instellingen bieden ook opmaakopties.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` eigenschap is afgekeurd. Gebruik `subtitlesOptions`-eigenschap van `PTMediaPlayerItem`. Zie [Ondertitels blootstellen](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md) om gesloten titels te gebruiken.