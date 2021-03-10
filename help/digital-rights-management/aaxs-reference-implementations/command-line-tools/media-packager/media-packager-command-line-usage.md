---
title: Gebruik van opdrachtregels
description: Gebruik van opdrachtregels
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---


# Gebruik van opdrachtregel {#command-line-usage}

Alvorens Media Packager te gebruiken, zorg ervoor dat u aan de vereisten voldoet die in Vereisten worden vermeld en dat het configuratiedossier de vereiste informatie bevat (zie het dossier van de Configuratie in *Gebruikend de Implementaties van de Verwijzing van de Toegang van de Adobe*.

Media Packager bevindt zich in de map [!DNL \Reference Implementation\Command Line tools] op de dvd. Gebruik de volgende syntaxis om één bestand te coderen:

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  source  
 <i class="+ topic ph hi-d="" i "="">
   dest [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `source` is het bestand dat moet worden gecodeerd.
* `dest` geeft aan waar de gecodeerde inhoud wordt geschreven. Als een map is opgegeven, wordt het gecodeerde bestand in deze map opgeslagen met dezelfde bestandsnaam als het bronbestand, maar de map mag niet de map zijn die het bronbestand bevat.

Gebruik de volgende syntaxis om meerdere bestanden met dezelfde sleutel (voor ondersteuning van meerdere bitsnelheden) te coderen:

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefiles  
 <i class="+ topic ph hi-d="" i "="">
   dest-directory [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `sourcefiles` is een reeks bronitems met als scheidingsteken een witruimte die de te coderen bestanden vertegenwoordigen.
* `dest-directory` geeft aan waar de gecodeerde inhoud wordt geschreven. De gecodeerde bestanden worden in deze map opgeslagen met dezelfde bestandsnamen als de bronbestanden, maar de map mag niet de map zijn die de bronbestanden bevat.

Gebruik de volgende syntaxis om informatie over een gecodeerd bestand weer te geven:

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

* `encryptedfile` is het gecodeerde bestand.

Gebruik de volgende syntaxis om informatie over een metagegevensbestand weer te geven:

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` is een  [!DNL .metadata] bestand met de DRM-metagegevens.

>[!NOTE]
>
>Tijdens het verpakken, zal de Packager van Media niet meer een .header dossier door gebrek produceren. Als u dit bestand wilt genereren, gebruikt u de optie `-h` tijdens het verpakken.

De volgende tabel bevat beschrijvingen van de opties voor de opdrachtregel die in de bovenstaande syntaxis worden getoond:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_wgz_spy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Opdrachtregeloptie </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-c <span class="+ topic/ph pr-d/codeph codeph"> configfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de locatie van het configuratiebestand op. Als deze optie niet wordt gebruikt zal Media Packager <span class="filepath"> flashaccess.properties </span> in de het werk folder zoeken. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> gecodeerd bestand </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee wordt informatie weergegeven over een bestand dat al in een pakket is opgenomen. De bron- en doelbestanden zijn niet vereist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier wordt informatie over bestaande metagegevens weergegeven. De bron- en doelbestanden zijn niet vereist. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gebruik deze optie met <span class="codeph"> -d </span> om beleid uit een verpakt dossier te halen. Er wordt een bestand gemaakt in dezelfde map als het gecodeerde bestand met de bestandsnaam en beleidsidentificatie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gebruik deze optie met <span class="codeph"> -d </span> om de DRM-header uit een verpakt bestand te extraheren. Er wordt een bestand gemaakt in dezelfde map als het gecodeerde bestand, met de bestandsnaam en de extensie <span class="filepath"> .header </span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee geeft u een unieke id voor dit stuk inhoud op. Als er geen id is opgegeven, wordt de bestandsnaam van het doelbestand gebruikt. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Geeft een aangepaste sleutel/waarde op die aan de metagegevens van de inhoud moet worden toegevoegd. Er kunnen meerdere <span class="codeph"> -k </span> opties worden opgegeven. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Gebruik deze optie bij <span class="codeph"> -d </span> om metagegevens uit een verpakt bestand te extraheren. Er wordt een bestand gemaakt in dezelfde map als het gecodeerde bestand met de bestandsnaam en de extensie <span class="codeph"> .metadata </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Vraag niet of het doelbestand moet worden overschreven. Als het doelbestand al bestaat en <span class="codeph"> -o </span> niet is ingesteld, wordt een fout geretourneerd. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hiermee overschrijft u het doelbestand zonder dat u hierom wordt gevraagd, als dit al bestaat. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> bestandsnaam [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Hier geeft u de naam op van het bestand dat het beleid bevat. Als het beleid domeinregistratie met een server vereist die een verschillend vervoercertificaat dan gespecificeerd in het bezitsdossier gebruikt, moet het certificaat van het domeinvervoer ook worden verstrekt. </p> <p class="- topic/p ">Er kunnen meerdere <span class="codeph"> -p </span> opties worden opgegeven en de client gebruikt de eerste standaard. De waarden die op de bevellijn worden gespecificeerd hebben belangrijkheid over die die in het configuratiedossier worden gespecificeerd. </p> </td> 
  </tr> 
 </tbody> 
</table>

