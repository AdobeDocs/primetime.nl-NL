---
description: De regel normaliseren definieert een URL-transformatie die moet worden toegepast op een creatieve bronURL die is verkregen uit een VAST/VMAP-reactie.
keywords: regel normaliseren;creatieve selectieregels
title: Regels normaliseren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

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
   <td>De waarde moet altijd <span class="codeph"> normaliseren</span>.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> host</span></td> 
   <td>Alleen op dit moment <span class="codeph"> host</span> wordt ondersteund. Dit kenmerk moet aanwezig zijn wanneer <span class="codeph"> overeenkomsten</span> en <span class="codeph"> waarden</span> kenmerken zijn gedefinieerd.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> overeenkomsten</span></td> 
   <td></td> 
   <td></td> 
   <td>Mogelijke waarden:
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> - gelijk</li> 
     <li><span class="codeph"> ne</span> - niet gelijk aan</li> 
     <li><span class="codeph"> co</span> - bevat</li> 
     <li><span class="codeph"> nc</span> - bevat niet</li> 
     <li><span class="codeph"> sw</span> - begint met</li> 
     <li><span class="codeph"> nieuw</span> - eindigt met</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> waarden</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td>TVSDK gebruikt de <span class="codeph"> overeenkomsten</span> kenmerk op de <span class="codeph"> item</span> van de bron creatief en gelijke met de waarden die in deze serie worden bepaald.</td> 
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
