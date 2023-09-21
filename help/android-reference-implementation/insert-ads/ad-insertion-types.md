---
description: De TVSDK biedt momenteel ingebouwde ondersteuning voor metagegevens van advertenties, directe ad-einden en aangepaste advertentiemarkeringen.
title: Toevoegingstypen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Toevoegingstypen {#ad-insertion-types}

De TVSDK biedt momenteel ingebouwde ondersteuning voor metagegevens van advertenties, directe ad-einden en aangepaste advertentiemarkeringen.

De volgende typen werkstromen voor het invoegen van advertenties worden ondersteund voor VOD en live/lineaire inhoud.

<table id="table_1C3A659BDDB7453CA953A103045FCA01"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Type invoeging </th> 
   <th colname="col2" class="entry"> Ondersteund in... </th> 
   <th colname="col3" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Adobe Primetime en beslissingsadvertenties </td> 
   <td colname="col2">VOD <p>Live </p> <p>Lineair </p> </td> 
   <td colname="col3">De referentie-implementatie biedt <span class="codeph"> AuditudeMetadata</span> informatie om met de server voor Primetime en besluit (vroeger genoemd geworden Auditude) te verbinden, die op de informatie wordt gebaseerd die in het gedeelte van de Advertenties van de Primetime wordt verstrekt</a> van het JSON-configuratiebestand</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Direct advertentie-einden </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">U moet advertentie-URL's opgeven in het JSON-invoerbestand. Wanneer de TVSDK een advertentie probeert op te lossen, wordt de directe en break-oplosser aangeroepen en worden de advertenties opgelost op basis van de informatie over directe ad-einden die in het JSON-configuratiebestand is opgegeven</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Aangepaste advertentiemarkeringen </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Aangepaste advertentiemarkeringen zijn handig wanneer de videostream zowel hoofdinhoud als advertenties bevat, maar geen informatie over de advertentiepunten en -timing bevat. Als de informatie over het plaatsen van de advertentie op een andere manier wordt verkregen, bijvoorbeeld via een extern CMS, kunt u aangepaste advertentiemarkeringen definiëren en deze doorgeven aan de tijdlijn van de speler. <p>Als u een speler wilt instellen voor invoeging in een advertentie, moet u metagegevens en metagegevens doorgeven in het gedeelte Aangepaste en metagegevens van het JSON-configuratiebestand</a>, die in de referentie-implementatie een ondersteunende ad-provider heeft. </p> </td>
  </tr>
 </tbody>
</table>
