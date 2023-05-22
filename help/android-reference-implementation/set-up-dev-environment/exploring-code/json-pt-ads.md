---
title: JSON-object voor primetime-advertenties
description: In het codeblok hieronder worden de details van het JSON-object gedefinieerd als de typewaarde bestaat uit primetime-advertenties.
exl-id: b1392781-2dfb-4934-b1ce-1c761cbfb22d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# JSON-object voor primetime-advertenties {#json-object-for-primetime-ads}

In het codeblok hieronder worden de details van het JSON-object gedefinieerd als de typewaarde bestaat uit primetime-advertenties.

```
“metadata”: {
    “ad” :  {
        “type”: “Primetime ads”,
        “details”: {
            "domain": "sandbox2.auditude.com",
            "mediaid": "rom_asset_case_1",
            "zoneid": "109754",
            "targeting": [
                {
                    "key": "osmfKeyMulAdsAvail12346",
                    "value": "MulAdsAvail12346"
                }
            ]
        }
    }
}
```

| Eigenschap | Beschrijving |
|---|---|
| domein | Het domein voor primetime-advertenties dat moet worden gebruikt voor advertentieverzoeken. |
| middelmatig | De mediaclip die voor deze inhoud is ingesteld in primetime-advertenties. |
| zoneid | De Primetime-advertenties zijn gezoneid. Raadpleeg de documentatie bij primetime-advertenties voor meer informatie. |
| doelgericht | Een array van sleutel-/waardeparen die wordt gebruikt voor het aanwijzen van specifieke advertenties voor de inhoud. |

Zie [com.adobe.mediacore.metadata.AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/metadata/AuditudeSettings.html) voor meer informatie over de waarde van deze eigenschappen.
