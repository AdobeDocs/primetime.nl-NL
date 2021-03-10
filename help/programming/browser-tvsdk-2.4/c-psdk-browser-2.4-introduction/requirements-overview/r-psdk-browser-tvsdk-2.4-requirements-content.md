---
description: Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests).
title: Inhoud- en manifestvereisten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Inhoud- en manifestvereisten{#content-and-manifest-requirements}

Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests).

<table id="table_D7C38CD3B4D24C3D9A3B55D8CEFE7366"> 
 <tbody> 
  <tr> 
   <td colname="col1"> Duur van inhoudssegment </td> 
   <td colname="col2"> De duur van een segment mag de doelduur niet overschrijden die in het manifestbestand is opgegeven. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Inhoudsvereiste </td> 
   <td colname="col2"> Elk TS segment zou met een zeer belangrijk kader moeten beginnen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> HLS-inhoud </td> 
   <td colname="col2"> <p>Houd rekening met het volgende: 
     <ul id="ul_B226605345EA46F69DA1380E16826117"> 
      <li id="li_6564DC0E879544BB8513DD2D1CFBA8DE">AAC-SSR-audio wordt niet ondersteund. </li> 
      <li id="li_B73CAEBE4347406EA4DB25551B444BDA">Audiocodecs AC3 en Enhanced AC3 worden niet ondersteund. </li> 
      <li id="li_5986DD33C0FE485D99D4C00E2E6012CA">HLS-streams met discontinuïteit, maar geen discontinuïtiemarkeringen worden niet ondersteund. </li> 
      <li id="li_FED8686372DF4A39BAABC531BA4EB137">HLS Live ondersteunt de rollover van het tijdstempel niet. </li> 
      <li id="li_565CFBEAD9874BA48F6E25B0893BF131">Advertenties in het DVR-venster van HLS Live streams worden niet opgelost. </li> 
      <li id="li_7D22EA32C94240D79EDDA96D9E72FE8F">Bytebereik wordt niet ondersteund met gecodeerde AES-128-inhoud. </li> 
     </ul></p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> DASH-gehalte </td> 
   <td colname="col2"> <p>Houd rekening met het volgende: 
     <ul id="ul_9D33C2418F9F49DEAE0E642301726F89"> 
      <li id="li_74C69A21A7BD4831B92F0D57900E1CB1">Voor live streams - Het live profiel met een dynamisch type wordt ondersteund. </li> 
      <li id="li_0C8743DB152047819D23C9F180998AD7">Voor VOD-streams - Het liveprofiel met het type static wordt ondersteund. </li> 
      <li id="li_FBC6828663FB413798A4BDAF0B9831AA">Voor VOD-streams - Het profiel op aanvraag is niet gecertificeerd voor ad-hocworkflows. </li> 
      <li id="li_4393B9B1F6144BDEAE484C879750ED23">Het afspelen van DASH-streams met meerdere punten wordt niet ondersteund. </li> 
      <li id="li_6A2CEC4E974C4D44A45F5503A1A9D8D0">Ingesloten bijschriften (608/708) die zijn gemarkeerd met de toegankelijkheidscode, worden ondersteund. </li> 
      <li id="li_EDE93DF4F3A64A53BA80877F701A8F0D">Fragmented/Segmented VTT-bestanden worden niet ondersteund. </li> 
      <li id="li_8897F73611194030A490A4FF1178364C">Streams met inband aangepaste tags worden niet gecertificeerd. </li> 
     </ul></p> </td> 
  </tr> 
 </tbody> 
</table>

