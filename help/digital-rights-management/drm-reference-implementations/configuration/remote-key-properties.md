---
title: Eigenschappen voor levering van externe sleutels (iOS)
description: Eigenschappen voor levering van externe sleutels (iOS)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Eigenschappen voor levering van externe sleutels (iOS){#remote-key-delivery-properties-ios}

Als u het genereren van licenties voor Remote Key-levering aan een iOS-client in Adobe Primetime DRM wilt ondersteunen, moet u het Key Server-certificaat opgeven in het bestand `flashaccess-refimpl.properties`.

De volgende eigenschappen zijn toegevoegd aan Primetime DRM:

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
   <td colname="2" class="- topic/entry "> <p>Certificaat van licentieserver van sleutelserver dat is uitgegeven door Adobe. </p> <p>Dit certificaat genereert licenties voor iOS-apparaten wanneer uit de metagegevens blijkt dat een sleutelserver vereist is. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>De alias van het Adobe-uitgegeven certificaat van de Server van een Sleutelserver van de Vergunning dat op HSM wordt opgeslagen. </p> <p>Wanneer u HSM toelaat, kunt u dit bezit in plaats van het <span class="codeph"> bezit toepassen HandlerConfiguration.KeyServerCertificate</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

