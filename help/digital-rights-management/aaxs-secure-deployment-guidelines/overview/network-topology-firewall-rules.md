---
seo-title: Firewall-regels
title: Firewall-regels
uuid: a5667030-c4d0-42e3-b56e-20a12c903954
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# Firewallregels {#firewall-rules}

## Binnenkomende URL&#39;s {#section-F111526A9DB844CBBF21A3CAE5F50880}

Vorm uw buitenfirewall zodat het slechts URLs voor toepassingsfunctionaliteit blootstelt die u aan het eind wilt verstrekken - gebruikers. Externe gebruikers alleen via de firewall toegang geven tot de URL&#39;s in de volgende tabel:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-bqs-whz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">URL van hoofdmap </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Doel </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/getServerVersion/v3</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL voor het bepalen van de serverversie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-xr4-hdn-44"> 
     <li id="li-05925A4DE4114F7786FF93A66AB8A117"><span class="filepath"> /flashaccess/authn/v1/*</span> </li> 
     <li id="li-E76E9BA0160F4E7F9EBB64428C2D9F31"><span class="filepath"> /flashaccess/authn/v3/*</span> </li> 
     <li id="li-ED3C15EB4D194FFE99954BDB7D5C1E41"><span class="filepath"> /flashaccess/authn/v4/*</span> </li> 
     <li id="li-4DD6CBBE939F4E6EABA474E3DCCBD893"><span class="filepath"> /flashaccess/authn/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL's voor gebruikersverificatie. Deze URL moet alleen toegankelijk zijn als u API's van de Adobe Access-client gebruikt voor het uitvoeren van gebruikersverificatie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-yxs-rdn-44"> 
     <li id="li-49B9987ED6E14FADA66727448F923F84"><span class="filepath"> /flashaccess/license/v1/*</span> </li> 
     <li id="li-BF4A415E573C4C728E24D548F53D923C"><span class="filepath"> /flashaccess/license/v3/*</span> </li> 
     <li id="li-E6C551DDA030429B9D0073D2685B778A"><span class="filepath"> /flashaccess/license/v4/*</span> </li> 
     <li id="li-57811F4CD7304DBDAFADD65244AED0D9"><span class="filepath"> /flashaccess/license/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL's voor het afgeven van licenties aan eindgebruikers. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-ibl-5dn-44"> 
     <li id="li-189BE370CD5044F988A42335C3BFE420"><span class="filepath"> /flashaccess/sync/v3</span> </li> 
     <li id="li-B333B85FFE8A46DD884595B0A620B4EE"><span class="filepath"> /flashaccess/sync/v4</span> </li> 
     <li id="li-E4771D3C5AA5454CA1EDCFAA3E027CC1"><span class="filepath"> /flashaccess/sync/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL's voor synchronisatieverzoeken. Deze URL moet alleen toegankelijk zijn als u de synchronisatievereisten opgeeft in uw licenties. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-plq-ydn-44"> 
     <li id="li-81C96F93BA904C8C95B907F1A77E6494"><span class="filepath"> /flashaccess/domain/v3</span> </li> 
     <li id="li-40F0952F09674CA3B9AAFB5A62F9D02E"><span class="filepath"> /flashaccess/domain/v4</span> </li> 
     <li id="li-3ADE44B959B548F8A31A6FF08537AF46"><span class="filepath"> /flashaccess/domain/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL's voor domeinregistratie. Deze URL moet alleen toegankelijk zijn als u domeinondersteuning implementeert. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-btm-c2n-44"> 
     <li id="li-3535EDF7C644406FAC471D4234C4AF98"><span class="filepath"> /flashaccess/dereg/v3</span> </li> 
     <li id="li-AB33657BC7E140E695767710DF7AEC72"><span class="filepath"> /flashaccess/dereg/v4</span> </li> 
     <li id="li-D15B32BCD4674269A3A2644DD5204707"><span class="filepath"> /flashaccess/dereg/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL's voor deregistratie van domein. Deze URL moet alleen toegankelijk zijn als u de domeinondersteuning implementeert. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/headerconversion/v1/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL's die door de client kunnen worden gebruikt om FMRMS 1.x DRM-metagegevens om te zetten in Adobe Access DRM-metagegevens. </p> <p class="- topic/p ">Opmerking: <i class="+ topic/ph hi-d/i ">Deze URL moet SSL (HTTPS)</i> gebruiken. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /edcws/services/urn:EDCLicenseService/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL van webservice LiveCycle Rights Management ES. Als inhoud is gepubliceerd met een eerdere versie van FMRMS, staat deze URL toe dat oudere clients verbinding maken met de server en worden gevraagd een upgrade uit te voeren naar Adobe Access. </p> <p class="- topic/p ">Opmerking: <i class="+ topic/ph hi-d/i ">Deze URL moet SSL (HTTPS)</i> gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/return/v5</span> </td> 
   <td colname="2" class="- topic/entry "> <p>URL's voor geretourneerde licenties. De URL moet alleen toegankelijk zijn als u ondersteuning voor het retourneren van licenties implementeert. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>De interne firewall mag alleen toestaan dat verbindingen worden gemaakt met de Adobe Access-licentieserver via de reverse-proxy en alleen met de hierboven vermelde URL&#39;s. Om scalability te verbeteren, zullen de verbindingen tussen de omgekeerde volmacht en de Toegang van Adobe over HTTP zijn.

## Uitgaande URL&#39;s {#section-FFF9F7BB353149F4A27F8788E9934A48}

De licentieserver vereist toegang via de firewall om de volgende CRL&#39;s van Adobe te downloaden:

* h<span></span>ttps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl
* ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl
* ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl
* ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl