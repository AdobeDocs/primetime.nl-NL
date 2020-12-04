---
description: De regel normaliseren definieert een URL-transformatie die moet worden toegepast op een creatieve bronURL die is verkregen uit een VAST/VMAP-reactie.
keywords: normalize rule;creative selection rules
seo-description: De regel normaliseren definieert een URL-transformatie die moet worden toegepast op een creatieve bronURL die is verkregen uit een VAST/VMAP-reactie.
seo-title: Regels normaliseren
title: Regels normaliseren
uuid: e2a11466-41a3-44ba-abec-1a541df6c1a1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 1%

---


# Regels normaliseren{#normalize-rules}

De regel normaliseren definieert een URL-transformatie die moet worden toegepast op een creatieve bronURL die is verkregen uit een VAST/VMAP-reactie.

## De regel normaliseren heeft de volgende kenmerken en mogelijke waarden:

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"> Sleutel</th> 
   <th class="entry"> Type</th> 
   <th class="entry"> Waarden</th> 
   <th class="entry"> Beschrijving</th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> normaliseren</span></td> 
   <td>De waarde moet altijd <span class="codeph"> normalize</span> zijn.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> host</span></td> 
   <td>Momenteel wordt alleen <span class="codeph"> host</span> ondersteund. Dit kenmerk moet aanwezig zijn wanneer <span class="codeph"> overeenkomsten</span> en <span class="codeph"> waarden</span> attributen worden bepaald.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> matches</span></td> 
   <td></td> 
   <td></td> 
   <td>Mogelijke waarden:
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - gelijk aan</li> 
     <li><span class="codeph"> ne</span> - niet gelijk aan</li> 
     <li><span class="codeph"> co</span> -contains</li> 
     <li><span class="codeph"> nc</span>  - niet bevat</li> 
     <li><span class="codeph"> sw</span> - begint met</li> 
     <li><span class="codeph"> nieuw</span> - eindigt met</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> waarden</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td>TVSDK gebruikt het <span class="codeph">-kenmerk </span> op het <span class="codeph">-item</span> van de bron-creatief en past dit aan op de waarden die in deze array zijn gedefinieerd.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> zoeken</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Een reguliere expressie die moet worden toegepast op de bron van de creatieve URL die moet overeenkomen.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> vervangen</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> Een reguliere expressie die op basis van de overeenkomst moet worden toegepast op de creatieve bronURL die moet worden vervangen.</td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                ...
                }
                {
                    "
<b>type</b>": "
<b>normalize</b>",
                    "
<b>item</b>": "host",
                    "
<b>matches</b>": "ew",
                    "
<b>values</b>": [
                        "redirector.gvt1.com"
                    ],
                    "
<b>find</b>": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "
<b>replace</b>": "videoplayback/$1/expire//$2/signature//"
                }                
            ]
        }
    }
}
```

