---
description: De regel normaliseren definieert een URL-transformatie die moet worden toegepast op een creatieve bronURL die is verkregen uit een VAST/VMAP-reactie.
keywords: normalize rule;creative selection rules
seo-description: De regel normaliseren definieert een URL-transformatie die moet worden toegepast op een creatieve bronURL die is verkregen uit een VAST/VMAP-reactie.
seo-title: Regels normaliseren
title: Regels normaliseren
uuid: ae0364d2-23e2-48d6-b9b6-869cd163080d
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Regels normaliseren {#normalize-rules}

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
   <td>De waarde moet altijd worden <span class="codeph"> genormaliseerd</span>.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> host</span></td> 
   <td>Momenteel wordt alleen de <span class="codeph"> host</span> ondersteund. Dit kenmerk moet aanwezig zijn wanneer kenmerken voor <span class="codeph"> overeenkomsten</span> en <span class="codeph"> waarden</span> worden gedefinieerd.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> matches</span></td> 
   <td></td> 
   <td></td> 
   <td>Mogelijke waarden:
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - gelijk</li> 
     <li><span class="codeph"> ne</span> - niet gelijk aan</li> 
     <li><span class="codeph"> co</span> - contains</li> 
     <li><span class="codeph"> nc</span> - bevat niet</li> 
     <li><span class="codeph"> sw</span> - begint met</li> 
     <li><span class="codeph"> nieuw</span> - eindigt met</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td>TVSDK gebruikt het kenmerk <span class="codeph"> match</span> op het <span class="codeph"> item</span> van de bron creatief en komt overeen met de waarden die in deze array zijn gedefinieerd.</td> 
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

