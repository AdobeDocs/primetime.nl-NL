---
title: Eigenschappen van licentieserver
description: Eigenschappen van licentieserver
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Eigenschappen van licentieserver {#license-server-properties-file}

Gebruik de [!DNL flashaccess-refimpl.properties] bestand voor het configureren van de licentieservercomponent van de referentie-implementatie. Minstens, ben zeker om de eigenschappen met betrekking tot de Credentials van het Vervoer en de Referentie van de Server van de Vergunning te vormen. De locaties van de referentiebestanden moeten worden opgegeven ten opzichte van de map die door de `config.resourcesDirectory` eigenschap. Dit bestand bevat ook diverse eigenschappen die gerelateerd zijn aan het verpakken van inhoud: deze eigenschappen worden alleen gebruikt voor de conversie van metagegevens van Flash Media Rights Management Server 1.x. Als u een van de waarden in dit eigenschappenbestand wijzigt, moet u de licentieserver opnieuw starten om de wijzigingen van kracht te laten worden.

Om het genereren van licenties voor externe sleutellevering aan iOS-clients in Adobe Access te ondersteunen, moet het sleutelservercertificaat worden opgegeven in [!DNL flashaccess-refimpl.properties].

De volgende eigenschappen zijn toegevoegd in de Toegang van de Adobe:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_xz2_lwy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Eigenschap </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> </td> 
   <td colname="2" class="- topic/entry "> Certificaat van licentieserver van sleutelserver, uitgegeven door Adobe. Dit certificaat wordt gebruikt om licenties voor iOS-apparaten te genereren, wanneer de metagegevens aangeven dat een sleutelserver is vereist. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">Alias of Key Server's door Adobe uitgegeven licentieservercertificaat dat is opgeslagen op HSM. Wanneer HSM is ingeschakeld, gebruikt u deze eigenschap in plaats van <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </td> 
  </tr> 
 </tbody> 
</table>
