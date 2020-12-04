---
description: 'Houd rekening met de volgende typen URL''s wanneer u uw firewallregels bepaalt '
seo-description: 'Houd rekening met de volgende typen URL''s wanneer u uw firewallregels bepaalt '
seo-title: Firewall-regels
title: Firewall-regels
uuid: 309b35b5-8c0a-4cd7-9289-b6b035955697
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Firewallregels {#firewall-rules}

Houd rekening met de volgende typen URL&#39;s wanneer u uw firewallregels bepaalt:

## Binnenkomende URL&#39;s {#section_F111526A9DB844CBBF21A3CAE5F50880}

U kunt uw buitenfirewall zodanig configureren dat alleen de URL&#39;s worden weergegeven voor de toepassingsfunctionaliteit die u aan eindgebruikers wilt verschaffen.

Externe gebruikers hebben toegang tot de volgende URL&#39;s via de buitenste firewall:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_bqs_whz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">URL van hoofdmap </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Doel </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/getServerVersion/v3</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Om de serverversie te bepalen. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_xr4_hdn_44"> 
     <li id="li_8C68877B0FAF427490BF826FB12BE2F2"><span class="filepath"> /flashaccess/authn/v1/*</span> </li> 
     <li id="li_BF44753FF42E40BD911D04996B962188"><span class="filepath"> /flashaccess/authn/v3/*</span> </li> 
     <li id="li_9B633CDDB3844644BD8E3BFE80FD1672"><span class="filepath"> /flashaccess/authn/v4/*</span> </li> 
     <li id="li_01B2E17BF4DB456383FD6E18E9DE28F5"><span class="filepath"> /flashaccess/authn/v5/*</span> </li> 
     <li id="li_096D349CCD7945B387CB80C3E99063C7"><span class="filepath"> /flashaccess/authn/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gebruikers verifiëren. </p> <p>Deze URL moet toegankelijk zijn als u Adobe Primetime DRM-client-API's gebruikt voor gebruikersverificatie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_yxs_rdn_44"> 
     <li id="li_4BEB80F46E8D4D0F90F9998AB7FAAEB7"><span class="filepath"> /flashaccess/license/v1/*</span> </li> 
     <li id="li_20DDE5B03284436F9DEF794867AFBC53"><span class="filepath"> /flashaccess/license/v3/*</span> </li> 
     <li id="li_6555F8689FF945338579C58DADC2E36D"><span class="filepath"> /flashaccess/license/v4/*</span> </li> 
     <li id="li_5112283BDCF1457099056733B633FAF1"><span class="filepath"> /flashaccess/license/v5/*</span> </li> 
     <li id="li_F73A570E2C1A45E1BBF21C1468B90D3A"><span class="filepath"> /flashaccess/license/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Om licenties aan eindgebruikers uit te geven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_ibl_5dn_44"> 
     <li id="li_3B984F500F6848EDBBA5ADC570417E34"><span class="filepath"> /flashaccess/sync/v3</span> </li> 
     <li id="li_3204CF10D68C4FDB97E369BD63FA3C2B"><span class="filepath"> /flashaccess/sync/v4</span> </li> 
     <li id="li_2222D27F73D0421396A4F0E18140B3F9"><span class="filepath"> /flashaccess/sync/v5</span> </li> 
     <li id="li_18020B7CE36B4C209F65FF01A00B6737"><span class="filepath"> /flashaccess/sync/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Verzoeken synchroniseren. </p> <p>Deze URL moet toegankelijk zijn als u de synchronisatievereisten opgeeft in uw licenties. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_plq_ydn_44"> 
     <li id="li_61F51463E2BF4ABCA4F209754D8A8052"><span class="filepath"> /flashaccess/domain/v3</span> </li> 
     <li id="li_898E849D7EA24045978D35C336AEEAFE"><span class="filepath"> /flashaccess/domain/v4</span> </li> 
     <li id="li_CF7590FDAF694EDF9685434BE8EE10CA"><span class="filepath"> /flashaccess/domain/v5</span> </li> 
     <li id="li_CA73424FDFAA4BD8BBE2C1AD165D2C31"><span class="filepath"> /flashaccess/domain/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Domeinen registreren. </p> <p>Deze URL moet toegankelijk zijn als u domeinondersteuning implementeert. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_btm_c2n_44"> 
     <li id="li_8A0DC38312CB4D3DBD313B3DE089D39E"><span class="filepath"> /flashaccess/dereg/v3</span> </li> 
     <li id="li_5BA24F70381F465F832FF28925B622C1"><span class="filepath"> /flashaccess/dereg/v4</span> </li> 
     <li id="li_C761F14F3C97479CBA5C255739E01A28"><span class="filepath"> /flashaccess/dereg/v5</span> </li> 
     <li id="li_23A8AABE7499488EB61B7ED27CC65098"><span class="filepath"> /flashaccess/dereg/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Domeinregistratie ongedaan maken. </p> <p>Deze URL moet toegankelijk zijn als u domeinondersteuning implementeert. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/headerconversion/v1/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">De client toestaan om FMRMS 1.x DRM-metagegevens te converteren naar Primetime DRM-metagegevens. </p> <p>Opmerking:  Deze URL moet SSL (HTTPS) gebruiken. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /edcws/services/urn:EDCLicenseService/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL van webservice LiveCycle Rights Management ES. Als inhoud is gepubliceerd met een eerdere versie van FMRMS, staat deze URL oudere clients toe verbinding te maken met de server. Deze clients worden gevraagd een upgrade uit te voeren naar Adobe Primetime DRM. </p> <p class="- topic/p ">Opmerking: Deze URL moet SSL (HTTPS) gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_382B69AB07204DD596BB375132224D96"> 
     <li id="li_24B4D42BECF8405281C73B782F8E7310"><span class="filepath"> /flashaccess/return/v5</span> </li> 
     <li id="li_6B79563205D1421F89131E650D71E83B"><span class="filepath"> /flashaccess/return/v6</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p>Licenties retourneren. </p> <p> De URL moet toegankelijk zijn als u ondersteuning voor het retourneren van licenties implementeert. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>De interne firewall mag alleen verbindingen met de Primetime DRM-licentieserver toestaan via de reverse-proxy en alleen met de URL&#39;s in de tabel. Om scalability te verbeteren, gebruik HTTP voor de verbindingen tussen de omgekeerde volmacht en Primetime DRM.

## Uitgaande URL&#39;s {#section_FFF9F7BB353149F4A27F8788E9934A48}

Met uitgaande URL&#39;s kan de licentieserver de CRL&#39;s downloaden van Adobe.

Hier volgt een lijst met de uitgaande URL&#39;s die u kunt gebruiken:

* `https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl`
* `https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl`
* `https://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl`
* `https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl`

