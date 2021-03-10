---
description: De de veiligheidskwetsbaarheid van het netwerk is onder de eerste bedreigingen aan om het even welke Internet-Onder ogen ziet of intranet-Onder ogen ziet toepassingsserver, en u moet gastheren op het netwerk tegen deze kwetsbaarheden onderdrukken.
title: Netwerklaagbeveiliging
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Netwerklaagbeveiliging{#network-layer-security}

De de veiligheidskwetsbaarheid van het netwerk is onder de eerste bedreigingen aan om het even welke Internet-Onder ogen ziet of intranet-Onder ogen ziet toepassingsserver, en u moet gastheren op het netwerk tegen deze kwetsbaarheden onderdrukken.

Hier zijn sommige gemeenschappelijke technieken die kwetsbaarheid van de netwerkveiligheid verminderen:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_djf_lhz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Techniek </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Gedemilitariseerde zones (DMZ's) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Segmentatie moet op minstens twee niveaus bestaan met de toepassingsserver die wordt gebruikt om Adobe Primetime DRM uit te voeren wanneer Primetime DRM zich achter de binnenfirewall bevindt. U moet het externe netwerk van DMZ scheiden die de Webservers omvat, en de Webservers moeten van het interne netwerk worden gescheiden. U kunt firewalls gebruiken om deze lagen van scheiding uit te voeren. </p> <p>U kunt het verkeer categoriseren en controleren dat door elke netwerklaag overgaat om ervoor te zorgen dat slechts het absolute minimum van vereiste gegevens wordt toegestaan. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Persoonlijke IP-adressen </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De Vertaling van het Adres van het Netwerk van het gebruik (NATIONAAL) met RFC 1918 privé IP adressen op de toepassingsservers van Primetime DRM. U kunt privé IP adressen (10.0.0.0/8, 172.16.0.0/12 en 192.168.0.0/16) toewijzen om het voor een aanvaller moeilijker te maken om verkeer aan en van een NATIONAAL interne gastheer door Internet te leiden. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Vuurmuren </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hieronder volgen enkele criteria die u in acht moet nemen wanneer u een firewalloplossing selecteert: </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul_wjf_lhz_n4"> 
      <li class="- topic/li " id="li_A620D0B635384590BA7804F9720D04D0">Voer firewalls uit die volmachtsservers en/of stateful inspectie, in plaats van eenvoudige pakket-filtrerende oplossingen steunen. </li> 
      <li class="- topic/li " id="li_3E4F814A30C047539185C23F4F57C282">Gebruik een firewall die een veiligheidsparadigma steunt waarin u alle diensten, behalve de uitdrukkelijk toegelaten diensten kunt ontkennen. </li> 
      <li class="- topic/li " id="li_96160B3F14C4425397F017AF93FABE32">Voer een firewalloplossing uit die dubbel-homed of multi-homed is. Deze architectuur biedt het grootste beveiligingsniveau en voorkomt dat onbevoegde gebruikers de firewallbeveiliging omzeilen. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

