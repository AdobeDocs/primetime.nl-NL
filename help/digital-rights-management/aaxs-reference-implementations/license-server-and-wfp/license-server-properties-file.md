---
title: Eigenschappen van licentieserver
description: Eigenschappen van licentieserver
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Bestand met eigenschappen van licentieserver {#license-server-properties-file}

Gebruik het [!DNL flashaccess-refimpl.properties] dossier om de component van de Server van de Vergunning van de verwijzingsimplementatie te vormen. Minstens, ben zeker om de eigenschappen met betrekking tot de Credentials van het Vervoer en de Referentie van de Server van de Vergunning te vormen. De locaties van de referentiebestanden moeten worden opgegeven ten opzichte van de map die wordt opgegeven door de eigenschap `config.resourcesDirectory`. Dit bestand bevat ook diverse eigenschappen die te maken hebben met inhoud in een pakket: deze eigenschappen worden alleen gebruikt voor de conversie van Flash Media Rights Management Server 1.x-metagegevens. Als u een van de waarden in dit eigenschappenbestand wijzigt, moet u de licentieserver opnieuw starten om de wijzigingen van kracht te laten worden.

Voor ondersteuning van het genereren van licenties voor externe sleutellevering aan iOS-clients in Adobe Access, moet het sleutelservercertificaat worden opgegeven in [!DNL flashaccess-refimpl.properties].

De volgende eigenschappen zijn toegevoegd aan Adobe Access:

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
   <td colname="2" class="- topic/entry "> Certificaat van licentieserver van sleutelserver, uitgegeven door Adobe. Dit certificaat wordt gebruikt om licenties voor iOS-apparaten te genereren, wanneer uit de metagegevens blijkt dat een sleutelserver vereist is. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">Alias of Key Server's door Adobe uitgegeven licentieservercertificaat dat is opgeslagen op HSM. Wanneer HSM wordt toegelaten, gebruik dit bezit in plaats van <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </td> 
  </tr> 
 </tbody> 
</table>

