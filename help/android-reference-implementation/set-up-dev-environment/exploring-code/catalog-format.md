---
description: De Primetime-referentie-implementatie gebruikt een op JSON gebaseerde feed-indeling voor reacties. Dit formaat wordt geparseerd gebruikend een implementatie van de interface IFeedItemAdapter.
title: Catalogusindeling
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Catalogusindeling {#catalog-format}

De Primetime-referentie-implementatie gebruikt een op JSON gebaseerde feed-indeling voor reacties. Dit formaat wordt geparseerd gebruikend een implementatie van de interface IFeedItemAdapter.

>[!NOTE]
>
>Deze feed-indeling is de voorbeeldindeling die de referentie-implementatie gebruikt en dient als voorbeeld van hoe de indeling kan worden geparseerd en toegewezen aan de feed-interface. U kunt uw eigen invoervoederindeling gebruiken met uw eigen implementaties van de voederinterface.

Op een hoog niveau bestaat de indeling uit een array met inhoudsvermeldingen. Elk item vertegenwoordigt een live of VOD gepubliceerde video-inhoud:

```
{
    "entries": [
        {
        },
        {
        },
        ...
    ]
}
```

Elke feed-invoer is een JSON-object met een bepaalde set kenmerken:

```
{
    "entries": [
        
            "id": "episode1",
            "title": "My episode1",
            "description": "This is an episode.",
            "categories": "documentary, educational, children",
            "keywords": "List, of, comma, separated, keywords",
            "isLive": false,
            "content":  [
                
                },
                
                },
            ],
            "thumbnails": [
                
                },
                
                }
            ]
            "metadata": 
            } 
        }
    ]
}
```

| Eigenschap | Beschrijving |
|---|---|
| `id` | Een unieke id/hulplijn voor de inhoud die is ingesteld door het publicatiesysteem voor de feed. |
| `title` | Een titel voor de inhoud. |
| `description` | Een beschrijving van de inhoud. |
| `categories` | Een lijst met categorieën die zijn gelabeld voor de inhoud die door de toepassing kan worden gebruikt om de gebruikerservaring te verbeteren. Lees deze in de eigenschappen voor de inhoud. |
| `keywords` | De toepassing kan een lijst met door komma&#39;s gescheiden trefwoorden gebruiken om de gebruikerservaring te verbeteren. Lees deze in de eigenschappen voor de inhoud. |
| `isLive` | true of false, Geeft aan of het een Live- of VOD-stream is. |
| `content` | Een array van JSON-objecten met alternatieve indelingen voor de inhoud samen met de bijbehorende URL&#39;s. Er kunnen bijvoorbeeld URL&#39;s zijn voor de indelingen f4m en m3u8. De JSON-objectkenmerken worden hieronder verder beschreven. |
| `thumbnails` | Een array van JSON-objecten met URL&#39;s voor verschillende miniatuurgrootten. De JSON-objectkenmerken worden hieronder gedefinieerd. |
| `metadata` | Een JSON-object dat metagegevens voor de inhoud definieert. Momenteel zijn deze metagegevens beperkt tot metagegevens die betrekking hebben op de inhoud. Het object metadata wordt hieronder gedefinieerd. |

Het volgende codeblok definieert de JSON-objecten die de array van **inhoudsobjecten**:

```
"content":  [
    {
        "format": "M3U8",
        "url": "https://adobeprimetime-f.akamaihd.net/i/
<i>longstringofcharacters</i>/
                 Episode_,640x360_1000,640x360_700,_b.mp4.csmil/master.m3u8",
        "language": "en"
    }  
],
```

| Eigenschap | Beschrijving |
|--- |--- |
| format | Moet de m3u8-indeling zijn voor Android. |
| url | De URL naar de videostream voor de opgegeven indeling. |

Het volgende codeblok definieert de JSON-objecten die de array van **miniatuurobjecten**:

```
"thumbnails": [
    {
        "format": "JPEG",
        "height":  "90",
        "width": "160",
        "url": "https://example.com/small.jpg"
    },
    {
        "format": "JPEG",
        "height": "450",
        "width": "800",
        "url": "https://example.com/large.jpg"
    }
],
```

| Eigenschap | Beschrijving |
|---|---|
| format | Een tekenreeks die de indeling van het miniatuurbestand aangeeft, bijvoorbeeld JPEG, PNG, enzovoort. |
| height | De hoogte van de miniatuur. In de referentietoepassing wordt de miniatuur met de kleinste hoogte en breedte geretourneerd als de kleine miniatuur en de miniatuur met de grootste breedte en hoogte als de grote miniatuur. |
| width | De breedte van de miniatuur. In de referentietoepassing wordt de miniatuur met de kleinste hoogte en breedte geretourneerd als de kleine miniatuur en de miniatuur met de grootste breedte en hoogte als de grote miniatuur. |
| url | De URL naar het miniatuurbestand. |

Het volgende codeblok definieert het **Object metadata**:

```
"metadata" : {
    "ad" : {
        "type" : "",
        "details" : {
        }
    }
    "entitlement" : {
        "id" : ""
    }
}
```

| Eigenschap | Beschrijving |
|--- |--- |
| advertentie | Toegevoegde metagegevens. |
| type | De waarde kan zijn Primetime Advertenties, Directe Advertentietekens, of de Markeringen van de Aangepaste Advertentie. <br/><br/>PSDK verstrekt ingebouwde steun voor de volgende types van meta-gegevens: Auditude-verwante meta-gegevens voor Primetime en het dienen (Primetime Advertentie), directe ad-einden met advertenties (Directe Ad Break), en douane ad tellers die de TimeRange voor elke advertentiemarkering (de Tellers van de Aangepaste Advertentie) verstrekken. Elk type heeft ingebouwde AdProvider in PSDK die de meta-gegevens verwerkt.  <br/><br/>De JSON-indeling voor elk van deze zijn hieronder gedefinieerd. |
| details | Bevat de kenmerken van de metagegevens van de advertentie. Beide typen metagegevens hebben hun eigen set kenmerken die hieronder worden gedefinieerd. Voor de ingebouwde types, bepalen de inbegrepen attributen de gegevens die door PSDK voor dat type worden verwacht. |
| toeschrijven | Metagegevens met betrekking tot rechten |
| id | Media resource-id die wordt gebruikt voor autorisatieaanvragen tegen de betaaltelevisieomroep van Adobe Primetime. De id kan een tekstreeks of een met HTML gecodeerde mRSS-tekenreeks zijn. Alle media-inhoud waarvoor toestemming vereist is, moet een geldige bron-id bevatten. |
