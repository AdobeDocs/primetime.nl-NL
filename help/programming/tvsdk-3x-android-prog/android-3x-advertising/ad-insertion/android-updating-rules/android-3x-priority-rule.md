---
description: De prioriteitsregel definieert de prioriteitsvolgorde van de ad-creatieven die worden geselecteerd voor afspelen vanaf een VAST/VMAP-respons.
keywords: prioriteitsregel;creatieve selectieregels
title: Prioriteitsregels
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 1%

---


# Prioriteitsregels {#priority-rules}

De prioriteitsregel definieert de prioriteitsvolgorde van de ad-creatieven die worden geselecteerd voor afspelen vanaf een VAST/VMAP-respons.

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"><b>Sleutel</b></th> 
   <th class="entry"><b>Type</b></th> 
   <th class="entry"><b>Waarden</b></th> 
   <th class="entry"><b>Beschrijving</b></th>
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
   <td>Momenteel wordt alleen <span class="codeph"> host</span> ondersteund. Dit kenmerk moet aanwezig zijn wanneer <span class="codeph"> overeenkomsten</span> en <span class="codeph"> waarden</span> attributen worden bepaald.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> matches</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> meerdere</span></td> 
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
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> prioriteit</span></td> 
   <td>De waarde moet altijd <span class="codeph"> prioriteit</span> zijn</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> waarden</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> <p>TVSDK gebruikt het <span class="codeph">-kenmerk </span> op het <span class="codeph">-item</span> van de bron en past zich aan de waarden in deze array aan</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td></td> 
   <td> <p>Waarde kan <span class="codeph"> vod</span> of <span class="codeph"> live</span> zijn</p> </td> 
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
