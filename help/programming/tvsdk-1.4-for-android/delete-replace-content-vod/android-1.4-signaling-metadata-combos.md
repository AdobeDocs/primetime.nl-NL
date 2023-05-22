---
description: U kunt tijdbereiken in VOD-streams markeren, verwijderen en vervangen door verschillende combinaties van ad-signaalmodus en metagegevens te gebruiken. Verschillende combinaties van signaalmodus en metagegevens resulteren in verschillende gedragingen.
title: Effect op het toevoegen en verwijderen van gegevens uit de advertentiemodus en combinaties van metagegevens
exl-id: 0b265471-2d5c-432b-b1c9-c850ce99f2f5
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Effect op het toevoegen en verwijderen van gegevens uit de advertentiemodus en combinaties van metagegevens{#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

U kunt tijdbereiken in VOD-streams markeren, verwijderen en vervangen door verschillende combinaties van ad-signaalmodus en metagegevens te gebruiken. Verschillende combinaties van signaalmodus en metagegevens resulteren in verschillende gedragingen.

>[!NOTE]
>
>Wanneer er een conflict tussen tijdwaaiers en ad signalerende wijzen is, geeft TVSDK de prioriteit van tijdwaaiers.

**Tabel 3: Handeling signaalmodus/combinatie van metagegevens**

<table>  
 <thead> 
  <tr> 
   <th class="entry"> Ad-signaalmodus </th> 
   <th class="entry"> Metagegevens toevoegen </th> 
   <th class="entry"> Gemaakte oplossingen </th> 
   <th class="entry"><span class="codeph"> PlacementInformations</span> gemaakt </th> 
   <th class="entry"> Resulterend gedrag </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <b>Servertoewijzing</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> Verwijderen </td> 
   <td> Verwijderen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Verwijderde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Verwijderen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), </span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> Bereiken verwijderd, advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Toegevoegde advertenties </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Vervangen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Vervangen bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Gemarkeerde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> CustomAd, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Bereiken gemarkeerd, geen advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td> <b>Manifest Cues</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </td> 
   <td> Toegevoegde advertenties </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Verwijderen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> Bereiken verwijderd, advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> Mark, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Bereiken gemarkeerd, geen advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Verwijderen </td> 
   <td> Verwijderen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Verwijderde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Gemarkeerde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Vervangen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Vervangen bereiken </td> 
  </tr> 
  <tr> 
   <td> <b>Aangepast tijdbereik</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Verwijderen </td> 
   <td> Verwijderen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Verwijderde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Verwijderen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Bereiken verwijderd, geen advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td> Geen </td> 
   <td> Geen advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Vervangen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Bereiken vervangen door advertenties </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Gemarkeerde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> Aangepaste advertentie, controle </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Bereiken gemarkeerd, geen advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td> <b>Niet ingesteld (standaard)</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Verwijderen </td> 
   <td> Verwijderen </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Verwijderde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Verwijderen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Bereiken verwijderd, advertenties ingevoegd </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Toegevoegde advertenties </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Vervangen, Auditude </td> 
   <td> Verwijderen, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Bereiken vervangen door advertenties </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Gemarkeerde bereiken </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> CustomAd, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Gemarkeerde bereiken </td> 
  </tr> 
 </tbody> 
</table>
