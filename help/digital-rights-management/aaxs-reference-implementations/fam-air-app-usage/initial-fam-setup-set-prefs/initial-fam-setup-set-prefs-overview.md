---
seo-title: Overzicht van voorkeuren instellen
title: Overzicht van voorkeuren instellen
uuid: d1c067b1-6c2b-460e-8d00-5a5bfee0789c
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Overzicht van voorkeuren instellen {#setting-preferences-overview}

Met uitzondering van de URL van de Packager Server worden alle hieronder opgegeven voorkeuren opgeslagen in het [!DNL flashaccess-refimpl-packager.properties] bestand op de server. Alle instellingen kunnen rechtstreeks in het eigenschappenbestand of via de AIR-toepassing worden gewijzigd. Wachtwoorden worden versleuteld wanneer ze worden opgeslagen in het eigenschappenbestand op de server. Typ het niet-gecodeerde wachtwoord in de gebruikersinterface en het wordt versleuteld voordat het in het bestand wordt opgeslagen.

>[!NOTE]
>
>Alle mappen en paden verwijzen naar mappen op de pakketserver, niet op de client waarop de AIR-toepassing wordt uitgevoerd.

Wijzigingen die u hier aanbrengt, worden onmiddellijk van kracht nadat u de voorkeuren hebt opgeslagen. U hoeft de server niet opnieuw te starten, tenzij de Packager Thread vanwege configuratieproblemen is afgesloten.

In de voorkeursbeschrijvingen worden de volgende termen gebruikt:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_tj5_hcz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Voorkeur </th> 
   <th colname="2" class="- topic/entry entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL van Packager Server </td> 
   <td colname="2" class="- topic/entry "> Locatie van server met <span class="filepath"> flashaccess-packager.war </span>; bijvoorbeeld <span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Resource Directory </td> 
   <td colname="2" class="- topic/entry "> Map met beleidsregels, certificaten, referenties en andere bronnen die vereist zijn voor de pakketserver </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL licentieserver </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL van de server waarvan de client een licentie moet aanvragen; bijvoorbeeld <span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

