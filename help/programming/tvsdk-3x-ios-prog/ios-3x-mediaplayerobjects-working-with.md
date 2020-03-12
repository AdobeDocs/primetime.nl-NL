---
description: Het PTMediaPlayer-object vertegenwoordigt uw mediaspeler. Een PTMediaPlayerItem vertegenwoordigt audio of video op uw speler.
seo-description: Het PTMediaPlayer-object vertegenwoordigt uw mediaspeler. Een PTMediaPlayerItem vertegenwoordigt audio of video op uw speler.
seo-title: Werken met MediaPlayer-objecten
title: Werken met MediaPlayer-objecten
uuid: 0c33ebd6-b11a-4e62-8c1c-880cfceff474
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Werken met MediaPlayer-objecten {#work-with-mediaplayer-objects}

Het PTMediaPlayer-object vertegenwoordigt uw mediaspeler. Een PTMediaPlayerItem vertegenwoordigt audio of video op uw speler.

## Informatie over de klasse MediaPlayerItem {#section_B6F36C0462644F5C932C8AA2F6827071}

Nadat een media middel met succes wordt geladen, leidt TVSDK tot een geval van de `PTMediaPlayerItem` klasse om toegang tot dat middel te verlenen.

De `PTMediaPlayer` mediabron verhelpt, laadt het bijbehorende manifestbestand en parseert het manifest. Dit is het asynchrone gedeelte van het proces voor het laden van bronnen. De `PTMediaPlayerItem` instantie wordt geproduceerd nadat het middel is opgelost, en deze instantie is een opgeloste versie van een media middel. TVSDK biedt toegang tot de nieuwe `PTMediaPlayerItem` instantie via `PTMediaPlayer.currentItem`.

>[!TIP]
>
>U moet wachten tot de bron is geladen voordat u het item van de mediaspeler opent.

## Levenscyclus van MediaPlayer-objecten {#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

Vanaf het moment dat u de `PTMediaPlayer` instantie maakt tot het moment waarop u de instantie beëindigt (opnieuw gebruikt of verwijdert), voltooit deze instantie een reeks overgangen van de ene status naar de andere.

Sommige bewerkingen zijn alleen toegestaan wanneer de speler zich in een bepaalde toestand bevindt. Aanroepen `play` in `PTMediaPlayerStatusCreated` is bijvoorbeeld niet toegestaan. U kunt deze status alleen aanroepen nadat de speler de `PTMediaPlayerStatusReady` status heeft bereikt.

Werken met statussen:

* U kunt de huidige status van het MediaPlayer-object ophalen met `PTMediaPlayer.status`.
* De lijst met statussen wordt gedefinieerd in `PTMediaPlayerStatus`.

Overgangsdiagram voor de levenscyclus van een instantie MediaPlayer:
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-ios2_web.png)

De volgende tabel bevat aanvullende gegevens:

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>PTMediaPlayerStatus</b></th> 
   <th colname="col2" class="entry"><b>Vindt plaats wanneer</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCreated</span> </p> </td> 
   <td colname="col2"> <p>Uw toepassing heeft een nieuwe mediaspeler aangevraagd door playerWithMediaPlayerItem <span class="codeph"></span>aan te roepen. De nieuwe speler wacht op het opgeven van een mediaspeler-item. Dit is de beginstatus van de mediaspeler. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>Uw toepassing roept <span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span>aan en de mediaspeler laadt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>TVSDK heeft het mediaspeleritem ingesteld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>De inhoud wordt voorbereid en de advertenties zijn ingevoegd in de tijdlijn of de advertentieprocedure is mislukt. Het bufferen of afspelen kan beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>Uw toepassing heeft het afspelen <span class="codeph"></span>opgeroepen, dus TVSDK probeert de video af te spelen. Er kan sprake zijn van buffering voordat de video daadwerkelijk wordt afgespeeld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>Wanneer de media in de toepassing worden afgespeeld en gepauzeerd, beweegt de mediaspeler tussen deze status en <span class="codeph"> PTMediaPlayerStatusPplaying</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>De speler heeft het einde van de stream bereikt en het afspelen is gestopt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusStopped</span> </p> </td> 
   <td colname="col2"> <p>Uw toepassing heeft de mediaspeler uitgebracht, die ook alle bijbehorende bronnen vrijgeeft. U kunt deze instantie niet meer gebruiken </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusError</span> </p> </td> 
   <td colname="col2"> <p>Er is een fout opgetreden tijdens het proces. Een fout kan ook van invloed zijn op wat de toepassing daarna kan doen. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>U kunt de status gebruiken om feedback te geven over het proces (bijvoorbeeld een spinner in afwachting van de volgende statuswijziging) of om de volgende stap uit te voeren in het afspelen van de media, bijvoorbeeld wachten op de juiste status voordat u de volgende methode aanroept.