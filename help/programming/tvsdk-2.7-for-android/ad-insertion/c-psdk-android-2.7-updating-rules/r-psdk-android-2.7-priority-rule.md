---
description: De prioriteitsregel definieert de prioriteitsvolgorde van de ad-creatieven die worden geselecteerd voor afspelen vanaf een VAST/VMAP-respons.
keywords: prioriteitsregel;creatieve selectieregels
title: Prioriteitsregels
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Prioriteitsregels {#priority-rules}

De prioriteitsregel definieert de prioriteitsvolgorde van de ad-creatieven die worden geselecteerd voor afspelen vanaf een VAST/VMAP-respons.

## Een Prioriteitsregel heeft de volgende kenmerken en mogelijke waarden:

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
   <td>Alleen op dit moment <span class="codeph"> host</span> wordt ondersteund. Dit kenmerk moet aanwezig zijn wanneer <span class="codeph"> overeenkomsten</span> en <span class="codeph"> waarden</span> kenmerken zijn gedefinieerd.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> overeenkomsten</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> meerdere</span></td> 
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
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td><span class="codeph"> prioriteit</span></td> 
   <td>De waarde moet altijd <span class="codeph"> prioriteit</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> waarden</span></td> 
   <td><span class="codeph"> Array</span></td> 
   <td></td> 
   <td> <p>TVSDK gebruikt de <span class="codeph"> overeenkomsten</span> kenmerk op de <span class="codeph"> item</span> van de bron creatief en gelijke met de waarden die in deze serie worden bepaald</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> stream</span></td> 
   <td><span class="codeph"> String</span></td> 
   <td></td> 
   <td> <p>Waarde kan <span class="codeph"> vod</span> of <span class="codeph"> leven</span></p> </td> 
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
