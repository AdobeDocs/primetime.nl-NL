---
seo-title: Voorbeeld van een aangepast VOD-element
title: Voorbeeld van een aangepast VOD-element
uuid: 25927d5f-ac16-45f4-bf0d-92f1ab394c05
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Voorbeeld van een aangepast VOD-element{#example-of-a-customized-vod-asset}

Hier volgt een voorbeeld van een aangepast VOD-element:

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:7
 
#EXT-X-ASSET:AID=10
 
#EXTINF:9.9766,
seg1.ts
 
#EXTINF:9.9766,
seg2.ts
 
#EXTINF:9.9766,
seg3.ts
 
#EXT-X-AD:DURATION=10
#EXTINF:9.9766,
seg4.ts
 
#EXTINF:9.9766,
seg5.ts
 
#EXT-X-ENDLIST
```

Uw toepassing kan de volgende scenario&#39;s instellen:

* Een melding wanneer het bestand `#EXT-X-ASSET` tags bevat of een andere set aangepaste tagnamen waarop u een abonnement hebt genomen.
* Voeg advertenties in wanneer er een `#EXT-X-AD` tag of een andere aangepaste tagnaam in de stream wordt gevonden.

