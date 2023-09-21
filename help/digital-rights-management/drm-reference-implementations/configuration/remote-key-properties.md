---
title: Eigenschappen voor levering van externe sleutels (iOS)
description: Eigenschappen voor levering van externe sleutels (iOS)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Eigenschappen voor levering van externe sleutels (iOS){#remote-key-delivery-properties-ios}

Als u het genereren van licenties voor levering op afstand aan een iOS-client in Adobe Primetime DRM wilt ondersteunen, moet u het sleutelservercertificaat opgeven in het dialoogvenster `flashaccess-refimpl.properties` bestand.

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
   <td colname="2" class="- topic/entry "> <p>Certificaat van de Server van de Vergunning van de zeer belangrijke server dat door Adobe wordt uitgegeven. </p> <p>Dit certificaat genereert licenties voor iOS-apparaten wanneer de metagegevens aangeven dat een Key Server is vereist. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>De alias van het Adobe-uitgegeven certificaat van de Server van een Sleutelserver dat op HSM wordt opgeslagen. </p> <p>Wanneer u HSM inschakelt, kunt u deze eigenschap toepassen in plaats van de eigenschap <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> eigenschap. </p> </td> 
  </tr> 
 </tbody> 
</table>
