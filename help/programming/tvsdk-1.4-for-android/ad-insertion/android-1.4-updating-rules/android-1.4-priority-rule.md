---
description: De prioriteitsregel definieert de prioriteitsvolgorde van de ad-creatieven die worden geselecteerd voor afspelen vanaf een VAST/VMAP-respons.
keywords: priority rule;creative selection rules
seo-description: De prioriteitsregel definieert de prioriteitsvolgorde van de ad-creatieven die worden geselecteerd voor afspelen vanaf een VAST/VMAP-respons.
seo-title: Prioriteitsregels
title: Prioriteitsregels
uuid: 6aa5822a-a3c0-49b2-b25b-0308a784e405
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Prioriteitsregels{#priority-rules}

De prioriteitsregel definieert de prioriteitsvolgorde van de ad-creatieven die worden geselecteerd voor afspelen vanaf een VAST/VMAP-respons.

**Tabel 1: Een Prioriteitsregel heeft de volgende kenmerken en mogelijke waarden:**

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
   <td><span class="codeph"> prioriteit</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> Een array van MIME-typen in kleine letters die de prioriteit definiëren waarin broncreatieven moeten worden geselecteerd voor afspelen.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> host</span></td> 
   <td>Momenteel wordt alleen de <span class="codeph"> host</span> ondersteund. Dit kenmerk moet aanwezig zijn wanneer kenmerken voor <span class="codeph"> overeenkomsten</span> en <span class="codeph"> waarden</span> worden gedefinieerd.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> matches</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> meerdere</span></td> 
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
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> prioriteit</span></td> 
   <td>De waarde moet altijd <span class="codeph"> prioriteit hebben</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> <p>TVSDK gebruikt het kenmerk <span class="codeph"> match</span> op het <span class="codeph"> item</span> van de bron creatief en komt overeen met de waarden die in deze array zijn gedefinieerd</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td></td> 
   <td> <p>Waarde kan leeg <span class="codeph"> of</span> <span class="codeph"> live zijn</span></p> </td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "
<b>type</b>": "
<b>priority</b>",
                    "
<b>stream</b>": "vod",
                    "
<b>priority</b>": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    ...
                },
            ]
        }
    }
}
```

