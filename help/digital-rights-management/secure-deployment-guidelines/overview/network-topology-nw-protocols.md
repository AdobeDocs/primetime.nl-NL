---
description: Wanneer u een veilige netwerkarchitectuur vormt, worden de netwerkprotocollen vereist voor interactie tussen Adobe Primetime DRM en andere systemen in uw ondernemingsnetwerk.
title: Adobe Primetime DRM-netwerkprotocollen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Adobe Primetime DRM-netwerkprotocollen {#adobe-primetime-drm-network-protocols}

Wanneer u een veilige netwerkarchitectuur vormt, worden de netwerkprotocollen vereist voor interactie tussen Adobe Primetime DRM en andere systemen in uw ondernemingsnetwerk.

Wanneer u een veilige netwerkarchitectuur vormt, worden de volgende netwerkprotocollen vereist voor deze interactie:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_itc_33z_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Protocol </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Gebruiken </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player-, Adobe AIR®- en Adobe Primetime-clients communiceren via HTTP met Primetime DRM. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS (optioneel) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player-, Adobe AIR- en Adobe Primetime-clients kunnen HTTPS gebruiken om te communiceren met Primetime DRM. HTTPS (SSL) is niet vereist, tenzij u FMRMS 1.x-clients ondersteunt. Zie <a href="../../secure-deployment-guidelines/overview/network-topology-firewall-rules.md" format="dita" scope="local"> Binnenkomende URL's </a> en SSL configureren voor meer informatie. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Poorten voor toepassingsservers {#ports-for-application-servers}

U kunt de Adobe Primetime DRM-licentieserver configureren voor gebruik van elke netwerkpoort.

Deze poorten moeten in- of uitgeschakeld zijn op de binnenfirewall, afhankelijk van de netwerkfunctionaliteit die u wilt toestaan voor clients die verbinding maken met de toepassingsserver waarop Primetime DRM wordt uitgevoerd.

## SSL {#configuring-ssl} configureren

De Secure Sockets Layer (SSL) is alleen nodig als u ondersteuning nodig hebt voor Flash Media Rights Management Server 1.x-clients.

SSL met clientverificatie is vereist voor de Adobe Primetime DRM Key Server. Zie [Adobe Primetime DRM Key Server gebruiken](../../using-the-drm-key-server/requirements.md) voor meer informatie.