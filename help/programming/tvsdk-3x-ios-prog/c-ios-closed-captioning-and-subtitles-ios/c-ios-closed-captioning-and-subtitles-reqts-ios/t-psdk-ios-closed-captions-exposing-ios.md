---
description: Als u Closed Captions beschikbaar wilt maken voor uw clientspeler, moet u deze inschakelen. De gebruiker kan Closed Captions in- of uitschakelen en de opmaak selecteren.
title: Gesloten bijschriften beschikbaar maken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
   >`closedCaptionDisplayEnabled` eigenschap is vervangen. Gebruiken `subtitlesOptions` eigenschap van `PTMediaPlayerItem`. Zie [Ondertiteling weergeven](../../../tvsdk-3x-ios-prog/c-ios-closed-captioning-and-subtitles-ios/c-ios-closed-captioning-and-subtitles-reqts-ios/t-ios-subtitles-exposing-ios.md) om gesloten bijschriften te gebruiken.
