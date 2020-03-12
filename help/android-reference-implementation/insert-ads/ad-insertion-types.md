---
description: De TVSDK biedt momenteel ingebouwde ondersteuning voor metagegevens van advertenties, directe ad-einden en aangepaste advertentiemarkeringen.
seo-description: De TVSDK biedt momenteel ingebouwde ondersteuning voor metagegevens van advertenties, directe ad-einden en aangepaste advertentiemarkeringen.
seo-title: Toevoegingstypen
title: Toevoegingstypen
uuid: 6b5c3555-1ddd-4215-8bb2-03d16bb818c5
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

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
   <td colname="col3">De verwijzingsimplementatie verstrekt <span class="codeph"> AuditudeMetadata</span> informatie om met de server voor Primetime en besluit (die eerder als Auditude wordt bekend) te verbinden, die op de informatie wordt gebaseerd die in het gedeelte</a> van de Advertentie van de Primetime van het JSON configuratiedossier</a>wordt verstrekt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Direct advertentie-einden </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">U moet advertentie-URL's opgeven in het JSON-invoerbestand. Wanneer de TVSDK een advertentie probeert op te lossen, wordt de directe en break-oplosser aangeroepen en worden de advertenties opgelost op basis van de informatie over directe ad-einden die in het JSON-configuratiebestand</a>is opgegeven. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Aangepaste advertentiemarkeringen </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Aangepaste advertentiemarkeringen zijn handig wanneer de videostream zowel hoofdinhoud als advertenties bevat, maar geen informatie over de advertentiepunten en -timing bevat. Als de informatie over het plaatsen van de advertentie op een andere manier wordt verkregen, bijvoorbeeld via een extern CMS, kunt u aangepaste advertentiemarkeringen definiëren en deze doorgeven aan de tijdlijn van de speler. <p>Als u een speler wilt instellen voor het invoegen van een advertentie, moet u metagegevens en metagegevens doorgeven in de sectie Aangepaste en metagegevens van het JSON-configuratiebestand</a>, dat een ondersteunende implementatie van een advertentieprovider in de referentie-implementatie bevat. </p> </td>
  </tr>
 </tbody>
</table>