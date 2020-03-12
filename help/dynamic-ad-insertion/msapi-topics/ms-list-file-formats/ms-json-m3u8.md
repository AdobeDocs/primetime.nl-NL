---
description: Als trackingmode=simple of ptplayer=ios-mobileweb, verzendt de manifestserver een JSON-bestand met Master-M3U8, een URL die de client moet gebruiken om het M3U8-bestand met een beschrijving van de inhoud aan te vragen.
seo-description: Als trackingmode=simple of ptplayer=ios-mobileweb, verzendt de manifestserver een JSON-bestand met Master-M3U8, een URL die de client moet gebruiken om het M3U8-bestand met een beschrijving van de inhoud aan te vragen.
seo-title: JSON-indeling voor URL voor het aanvragen van afspeellijst met variantmanifest
title: JSON-indeling voor URL voor het aanvragen van afspeellijst met variantmanifest
uuid: 9f9693d0-3c93-4555-b20c-7f4576742f41
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# JSON-indeling voor URL voor het aanvragen van afspeellijst met variantmanifest {#json-format-for-url-for-requesting-variant-manifest-playlist}

Als `pttrackingmode=simple` of `ptplayer=ios-mobileweb`, verzendt de manifestserver een JSON-Geformatteerd dossier dat hoofd-M3U8 bevat, een URL voor de cliënt aan gebruik om het M3U8- dossier te verzoeken beschrijvend de inhoud.

Dit is de indeling van het JSON-bestand met de `Master-M3U8` URL.

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
