---
description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-title: Bijhouden op fragmentniveau met behulp van laadgegevens
title: Bijhouden op fragmentniveau met behulp van laadgegevens
uuid: a6572823-d525-4ce0-806a-3feb20678cb0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Bijhouden op fragmentniveau met behulp van laadgegevens{#track-at-the-fragment-level-using-load-information}

De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.

TVSDK biedt ook informatie over de volgende gedownloade bronnen:

1. Afspeellijst-/manifestbestanden
1. Bestandsfragmenten
1. Gegevens bijhouden voor bestanden

   U kunt de kwaliteit van de dienst (QoS) informatie over gedownloade middelen, zoals fragmenten en sporen, van de `LoadInfo` klasse lezen.

1. Implementeer de callback-gebeurtenislistener `onLoadInfo`.
1. Registreer de gebeurtenislistener, die door TVSDK wordt aangeroepen telkens wanneer een fragment is gedownload.
1. Lees de gegevens van belang van de `LoadInfo` parameter die tot callback wordt overgegaan.

   <table id="table_06BD536A23AB4A73B510998426BAE143"> 
    <thead> 
      <tr> 
      <th colname="col01" class="entry"> Eigenschap </th> 
      <th colname="col1" class="entry"> Type </th> 
      <th colname="col2" class="entry"> Beschrijving </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> lang  </span> </td> 
      <td colname="col2"> <p>De duur van de download in milliseconden. </p> <p>TVSDK maakt geen onderscheid tussen de tijd dat de client verbinding heeft gemaakt met de server en de tijd die nodig was om het volledige fragment te downloaden. Bijvoorbeeld, als een 10 MB segment 8 seconden aan download vergt, verstrekt TVSDK die informatie, maar vertelt u niet dat het 4 seconden tot de eerste byte en nog eens 4 seconden kostte om het volledige fragment te downloaden. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> lang  </span> </td> 
      <td colname="col2"> De mediaduur van de gedownloade fragmenten in milliseconden. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> periodIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> De tijdlijntijdindex die is gekoppeld aan de gedownloade bron. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> size  </span> </td> 
      <td colname="col1"> <span class="codeph"> lang  </span> </td> 
      <td colname="col2"> De grootte van de gedownloade bron in bytes. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> de index van het overeenkomstige spoor, indien bekend; anders, 0. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackName  </span> </td> 
      <td colname="col1"> <span class="codeph"> String  </span> </td> 
      <td colname="col2"> de naam van de overeenkomstige spoorbaan, indien bekend; anders, null. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackType  </span> </td> 
      <td colname="col1"> <span class="codeph"> String  </span> </td> 
      <td colname="col2"> het type van het overeenkomstige spoor, indien bekend; anders, null. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> type  </span> </td> 
      <td colname="col1"> <span class="codeph"> String  </span> </td> 
      <td colname="col2"> Wat heeft TVSDK gedownload. Een van de volgende opties: 
      <ul id="ul_9C3BDEBD878544DA95C7FF81114F9B5C"> 
      <li id="li_A093552B492A44FD8B30785E465F6886">MANIFEST - Een afspeellijst/manifest </li> 
      <li id="li_DEF9AC71AA564F9BB4C5D4E834432EE5">FRAGMENT - Een fragment </li> 
      <li id="li_57821F47B6F04CD38570BCE6447A01B8">TRACK - Een fragment dat is gekoppeld aan een specifieke track </li> 
      </ul> Soms is het mogelijk dat het type van de bron niet kan worden gedetecteerd. Als dit gebeurt, wordt FILE geretourneerd. </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> url  </span> </td> 
      <td colname="col1"> <span class="codeph"> String  </span> </td> 
      <td colname="col2"> De URL die naar de gedownloade bron wijst. </td> 
      </tr> 
    </tbody> 
   </table>
