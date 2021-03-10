---
description: De TVSDK-speler verzendt gebeurtenissen om de status van de aangepaste advertentie en het laden weer te geven of om een advertentie te negeren die te lang duurt om te laden of die fouten bevat. Deze gebeurtenissen worden gedefinieerd in events.CustomAdEvents.
title: Aangepaste ad-events
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Aangepaste ad-events{#custom-ad-events}

De TVSDK-speler verzendt gebeurtenissen om de status van de aangepaste advertentie en het laden weer te geven of om een advertentie te negeren die te lang duurt om te laden of die fouten bevat. Deze gebeurtenissen worden gedefinieerd in events.CustomAdEvents.

<table id="table_718700E0F0B042F882ED131F79E01D4E"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gebeurtenis </th> 
   <th colname="col2" class="entry"> Definitie </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdClickThru  </span> </td> 
   <td colname="col2"> Het aantal keren dat de viewer op een aangepaste advertentie heeft geklikt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdError  </span> </td> 
   <td colname="col2"> Er is een fout opgetreden met de aangepaste advertentie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoaded  </span> </td> 
   <td colname="col2"> De aangepaste advertentie is geladen.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoading  </span> </td> 
   <td colname="col2"> De aangepaste advertentie wordt geladen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPaused  </span> </td> 
   <td colname="col2"> De aangepaste advertentie is gepauzeerd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdResumed  </span> </td> 
   <td colname="col2"> De aangepaste advertentie is na een pauze verder afgespeeld. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> Afspelen  </span> </td> 
   <td colname="col2"> De aangepaste advertentie wordt afgespeeld. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdProgress  </span> </td> 
   <td colname="col2"> <p>De aangepaste advertentiespeler informeert de TVSDK-speler over de voortgang van de aangepaste advertentie. &amp;nbsp; </p> <p>De <span class="codeph"> currentTime </span> en <span class="codeph"> totalTime </span> van de advertentie worden met deze gebeurtenis overgegaan. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStarted </td> 
   <td colname="col2"> De aangepaste advertentie is begonnen met afspelen en wordt weergegeven aan de viewer.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStopped </td> 
   <td colname="col2"> De aangepaste advertentie is afgespeeld. </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_027774C2A47C453BA9DED61C6F8567C3"></a>-->

