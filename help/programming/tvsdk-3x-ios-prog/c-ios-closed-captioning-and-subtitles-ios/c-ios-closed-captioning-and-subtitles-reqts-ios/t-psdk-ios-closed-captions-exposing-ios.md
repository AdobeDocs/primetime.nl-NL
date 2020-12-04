---
description: Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.
seo-description: Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.
seo-title: Gesloten bijschriften beschikbaar maken
title: Gesloten bijschriften beschikbaar maken
uuid: 7057014a-b14a-4790-8f7f-37d7a1fb8194
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
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
   >`closedCaptionDisplayEnabled` eigenschap is afgekeurd. Gebruik `subtitlesOptions`-eigenschap van `PTMediaPlayerItem`. Zie [Ondertitels blootstellen](../../../tvsdk-3x-ios-prog/c-ios-closed-captioning-and-subtitles-ios/c-ios-closed-captioning-and-subtitles-reqts-ios/t-ios-subtitles-exposing-ios.md) om gesloten titels te gebruiken.