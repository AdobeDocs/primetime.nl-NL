---
description: Als trackingmode=simple of ptplayer=ios-mobileweb, verzendt de manifestserver een JSON-bestand met Master-M3U8, een URL die de client moet gebruiken om het M3U8-bestand met een beschrijving van de inhoud aan te vragen.
title: JSON-indeling voor URL voor het aanvragen van afspeellijst met variantmanifest
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---


# JSON-indeling voor URL voor aanvragen van afspeellijst met variantmanifest {#json-format-for-url-for-requesting-variant-manifest-playlist}

Als `pttrackingmode=simple` of `ptplayer=ios-mobileweb`, de manifestserver een JSON-Geformatteerd dossier terugstuurt die Master-M3U8 bevatten, een URL voor de cliënt om het M3U8- dossier te verzoeken beschrijvend de inhoud te gebruiken.

Dit is de indeling van het JSON-bestand met de URL `Master-M3U8`.

```
{
"Master-M3U8": "https://manifest.auditude.com/auditude/variant/{publisherAssetID}/
  {sessionId}/{Base 64 of the url of the content}.m3u8
  ?u={Ad Request Id}
  &z={Ad Zone Id}
  &pttrackingmode=simple
  &pttrackingversion=v1
  &{other query parameters}"
}
```
