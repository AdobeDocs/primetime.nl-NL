---
description: Deze klassen bieden informatie over de tijdlijn van de specifieke media, waaronder de plaatsing van advertenties.
title: Tijdlijnklassen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Tijdlijnklassen{#timeline-classes}

Deze klassen bieden informatie over de tijdlijn van de specifieke media, waaronder de plaatsing van advertenties.

Pakket: [com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Naam </th> 
   <th colname="2" class="entry"> <p>Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/ContentTracker.html" format="html" scope="external"> ContentTracker  </a> </span> </td> 
   <td colname="2"> Interface die het protocol bepaalt dat u moet uitvoeren als u een inhoud-volgende module wilt tot stand brengen die wordt ontworpen om met de bibliotheek van TVSDK te integreren. <p>Deze interface vereist dat u definieert hoe voortgangsgebeurtenissen worden gerapporteerd aan het externe volgsysteem. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Opportunity.html" format="html" scope="external"> Opportunity  </a> </span> </td> 
   <td colname="2"> Basisklasse voor alle opportuniteitsklassen. Een opportuniteitsklasse staat voor een "interessant" punt op de tijdlijn. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Placement.html" format="html" scope="external"> Plaatsing  </a> </span> </td> 
   <td colname="2"> Klasse die informatie over tijdlijnplaatsing omvat. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementMode.html" format="html" scope="external"> PlacementMode  </a> </span> </td> 
   <td colname="2"> Opsomming van plaatsingsmodi, bijvoorbeeld of inhoud moet worden ingevoegd of vervangen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementType.html" format="html" scope="external"> PlacementType  </a> </span> </td> 
   <td colname="2"> Opsomming van plaatsingstypen die aangeven waar plaatsing in de tijdlijn plaatsvindt. bijvoorbeeld PRE_ROLL. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Reservation.html" format="html" scope="external"> Voorbehoud  </a> </span> </td> 
   <td colname="2"> Een reserve wordt gebruikt om verdere verwerking van een bepaalde tijdwaaier op de chronologie te beperken of te verhinderen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> Tijdlijn  </a> </span> </td> 
   <td colname="2"> Interface die een iterator voor het verwerken van tijdlijnmarkeertekens biedt. Geeft de tijdlijn van de inhoud aan, inclusief afbrekingen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem  </a> </span> </td> 
   <td colname="2"> Klasse. Algemene, onveranderlijke representatie van een tijdlijstitem. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker  </a> </span> </td> 
   <td colname="2"> Klasse die een markeerteken op de tijdlijn vertegenwoordigt. Dit markeert een gebied van belang op de daadwerkelijke chronologie. Momenteel zijn de interessegebieden de advertenties, die u bijvoorbeeld met een andere kleur op de scrub bar UI zou kunnen willen merken. Elke markering wordt gedefinieerd door een positie en een duur (elk uitgedrukt in milliseconden). </td> 
  </tr> 
 </tbody> 
</table>

