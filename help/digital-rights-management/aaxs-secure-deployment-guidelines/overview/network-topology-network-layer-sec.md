---
seo-title: Netwerklaagbeveiliging
title: Netwerklaagbeveiliging
uuid: bd53bccf-1130-4189-97ec-4259bd25762f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Netwerklaagbeveiliging{#network-layer-security}

De de veiligheidskwetsbaarheid van het netwerk is onder de eerste bedreigingen aan om het even welke Internet-Onder ogen ziet of intranet-Onder ogen ziet toepassingsserver. Deze sectie beschrijft het proces om gastheren op het netwerk tegen deze kwetsbaarheid te verharden. Het richt netwerksegmentatie, de stapelverharding van het Protocol van de Controle van de Transmissie/van Internet-protocol (TCP/IP), en het gebruik van firewalls voor gastheerbescherming.

Deze lijst beschrijft gemeenschappelijke technieken die de kwetsbaarheid van de netwerkveiligheid verminderen.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-djf-lhz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Techniek </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Gedemilitariseerde zones (DMZ's) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De segmentatie moet in minstens twee niveaus bestaan met de toepassingsserver die wordt gebruikt om Toegang in werking te stellen Adobe die achter de binnenfirewall wordt geplaatst. Scheid het externe netwerk van DMZ die de Webservers bevat, die beurtelings van het interne netwerk moeten worden gescheiden. Gebruik firewalls om de scheidingslagen te implementeren. Categoriseer en controleer het verkeer dat door elke netwerklaag overgaat om ervoor te zorgen dat slechts het absolute minimum van vereiste gegevens wordt toegestaan. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Persoonlijke IP-adressen </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De Vertaling van het Adres van het Netwerk van het gebruik (NATIONAAL) met RFC 1918 privé IP adressen op de toepassingsservers van de Toegang van Adobe. Wijs privé IP adressen (10.0.0.0/8, 172.16.0.0/12, en 192.168.0.0/16) toe om het voor een aanvaller moeilijker te maken om verkeer aan en van een NATIONAAL interne gastheer door Internet te leiden. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Vuurmuren </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gebruik de volgende criteria om een firewalloplossing te selecteren: </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul-wjf-lhz-n4"> 
      <li class="- topic/li " id="li-8031632160F44037B092988183139202"> <p class="- topic/p ">Voer firewalls uit die volmachtsservers en/of stateful inspectie in plaats van eenvoudige pakket-filtrerende oplossingen steunen. </p> </li> 
      <li class="- topic/li " id="li-B65CBB92113E4503B79EB194C34FCA50"> <p class="- topic/p ">Gebruik een firewall die een veiligheidsparadigma steunt waarin u alle diensten behalve die uitdrukkelijk kunt ontkennen toegelaten. </p> </li> 
      <li class="- topic/li " id="li-5CE4C7B65D84410DB4BE966FD8922993"> <p class="- topic/p ">Voer een firewalloplossing uit die dubbel-homed of multi-homed is. Deze architectuur biedt het grootste beveiligingsniveau en helpt te voorkomen dat onbevoegde gebruikers de firewallbeveiliging omzeilen. </p> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

